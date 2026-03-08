# Family-Justice-Review-Assistant
Family Justice Review Assistant
# Family Justice Review Assistant (FJRA) — Build Files

for examples you can see this is action in 
https://chatgpt.com/g/g-69adf0975db88191ba61fc5ce8b3470d-family-justice-review-assistant
https://gpt5-thinking-e64496-fjra.infinityfree.me/fjra-build/

This repository contains the **core “build artifacts”** used to create the **Family Justice Review Assistant (FJRA)** as a **Custom GPT** in ChatGPT:

- A **System Prompt** (the “operating rules” for the GPT)
- An **EWS file format / schema** (a fixed structure for court-ready Expert Witness Statements)

If you want to build your own GPT (either a fork of FJRA or a brand-new assistant), these files are the starting point.

---

## What’s in this repo

### 1) `GPT-System-Prompt`
**Purpose:** This is the *system-level instruction set* for the GPT.

A Custom GPT’s “Instructions” field is effectively its **system prompt**: it defines what the GPT *is*, what it *must do*, what it *must not do*, and what rules override everything else.

In FJRA, the system prompt is designed to make the GPT:

- Produce **court-ready Expert Witness Statements (EWS)**
- Follow a **strict, repeatable schema**
- Use a **zero-guessing** approach (avoid inventing facts)
- Treat user-provided/attached files as the evidentiary record
- Enforce formatting rules (especially around evidence tables, page numbering, and source filenames)

**When you would edit this file:**
- You want the GPT to generate a different kind of output (e.g., affidavits, chronologies, factums).
- You want different tone, safety rails, or workflow (e.g., “friendly drafting assistant” vs “strict evidence protocol”).
- You want to change how citations, page references, or verification logs work.

---

### 2) `EWS_FORMAT_25.MD`
**Purpose:** This file defines the **EWS schema** — a consistent format the GPT must follow every time.

FJRA’s EWS approach is:
- **Court-oriented**
- **Evidence-driven**
- **Structured into 25 top-level sections**
- Designed so a reader can quickly assess:
  - what happened,
  - what rights are implicated,
  - what evidence exists (and where),
  - what procedural issues occurred,
  - what remedies are sought.

A key concept in this schema is the **Section 10 evidence table** (and related verification steps). In practice, this makes outputs easier to audit and harder to dismiss as “unsupported narrative.”

**When you would edit this file:**
- You want a different statement structure (e.g., 10 sections, 12 sections, or a jurisdiction-specific template).
- You want to rename headings, add new required subsections, or change evidence-table columns.

---

## What is an “EWS file format” (in plain language)?

**EWS** = **Expert Witness Statement** (or an expert-style structured statement).

In this project, the “EWS file format” is a **repeatable template** that forces the GPT to write:

- in the same order every time,
- using the same headings,
- with an evidence table that can be checked against source documents.

Think of it like:
- a *court brief template* + 
- an *audit log* + 
- an *evidence index*.

This increases consistency and makes it easier to:
- review,
- challenge,
- verify,
- and reuse outputs across multiple events/issues.

---

## How the System Prompt and EWS schema work together

**System Prompt (`GPT-System-Prompt`)**
- Tells the GPT **how to behave**
- Defines mandatory rules (e.g., “use the EWS schema,” “don’t guess,” “label unverified claims”)

**EWS Schema (`EWS_FORMAT_25.MD`)**
- Tells the GPT **how to structure the output**
- Forces consistent headings, sections, and table formatting

Together, they form a “deterministic writing machine”:
> Same inputs → same structure → outputs that are easier to validate.

---

## Build your own GPT (recommended path)

### Step 1 — Open the GPT Builder
- GPT Editor (direct): https://chatgpt.com/gpts/editor  
- Explore GPTs (UI entry point): https://chatgpt.com/gpts

(You generally need a plan that supports building GPTs.)

### Step 2 — Create a new GPT
In the GPT editor:
1. Click **Create**
2. Give it a **name** (e.g., “My Court Statement Assistant”)
3. Add a short **description** (“Generates structured statements using a fixed evidence protocol.”)

### Step 3 — Paste the System Prompt
Open `GPT-System-Prompt` in this repository and paste it into the GPT’s **Instructions** field.

### Step 4 — Add the EWS schema as Knowledge
Upload `EWS_FORMAT_25.MD` to the GPT’s **Knowledge** section.

> Tip: For best results, keep schema files short, stable, and versioned.

### Step 5 — (Optional) Add more Knowledge files
You can add:
- court rules references
- your own templates
- a style guide
- jurisdiction-specific headings
- your own “event log” format

### Step 6 — Test with a small prompt
Example:
> “Using the EWS 25-section schema, generate an EWS for Event 16 based on the following text. Mark anything unverified.”

Then iterate:
- tighten formatting,
- adjust headings,
- enforce stricter citation behavior,
- add safety constraints.

---

## Project build guide (FJRA-specific)

If you’re specifically building **FJRA** (as designed by this project), see:

- Build guide site: https://gpt5-thinking-e64496-fjra.infinityfree.me/fjra-build/
- Repo home: https://github.com/paulcurtis26/Family-Justice-Review-Assistant

---

## Suggested repository conventions

If you’re forking/expanding:
- Keep the schema file(s) in the repo root:  
  - `EWS_FORMAT_25.MD`
- Keep prompts versioned (so outputs are reproducible):  
  - `GPT-System-Prompt`
  - `GPT-System-Prompt.v2` (optional)
- Add examples:
  - `examples/ews_event_16.md`
  - `examples/ews_blank_template.md`

---

## License

See `LICENSE` (Apache-2.0).

---

## Disclaimer

This project provides drafting/structuring assistance and does not constitute legal advice. Outputs must be reviewed by a qualified professional before court submission.
