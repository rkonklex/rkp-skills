---
description: "Structural audit of research documents. Auto-detects mode from argument: a directory path runs an architecture audit (inter-document content placement and boundaries); a file path runs a document audit (intra-document readability and layering). Produces a concrete restructuring plan as a handoff document for another agent to execute."
argument-hint: "<path> — file for document audit, directory for architecture audit. Flags: --document or --architecture to force a mode; --canonical <path> to specify the canonical reference explicitly."
disable-model-invocation: true
---

You are producing a structural restructuring plan. This plan will be handed off to another agent for execution — it must be concrete, unambiguous, and self-contained. The executing agent will not have access to this conversation.

Specify structural moves precisely enough that another agent can execute them without asking questions — a structural plan, not a content pass.

## Setup

**Parse arguments:**

- If `--document` is present, or if the path argument resolves to a file → **Mode A**.
- If `--architecture` is present, or if the path argument resolves to a directory → **Mode B**.

**Identify the canonical reference (both modes):**

If `--canonical <path>` was given, use that document as the canonical reference.

Otherwise, infer it:
1. Look for `AGENTS.md` and `README.md` in the target directory (the file's parent directory for Mode A, the directory itself for Mode B). Read whichever exist — they typically name the key documents and their roles.
2. If neither is found there, check the root project directory for the same files.
3. From what you read, identify the document described as the primary reference, canonical source, or most stable document. State your inference explicitly before proceeding.
4. If no clear canonical reference can be identified, proceed without one and note the absence in the plan.

---

## Mode A — Document Structural Audit

Read the target document in full.

Diagnose the following, in order:

**1. Document purpose and audience**
State in one sentence what this document is for and who reads it. If this is not clear from the document itself, flag it — a document without a clear purpose cannot be structured correctly.

**2. Layer analysis**
Identify what layers of detail are present and whether they are separated or interleaved. The expected progression is: orientation → conceptual model → detail → reference. Flag:
- Missing layers (e.g., no conceptual overview before dense detail)
- Collapsed layers (detail and reference mixed into the same section)
- Inverted layers (conclusions before argument, detail before orientation)

**3. Reading order vs. discovery order**
Identify sections or passages where the document reflects the order in which knowledge was discovered rather than the order a reader should acquire it. Flag:
- Forward references not signposted as such
- Structural inversions where a later section is required to understand an earlier one

**4. Digressions and historical material**
Flag passages that do not serve the document's stated purpose:
- Tangential background the reader does not need to act on the document
- References to superseded designs, prior attempts, or rationale for decisions no longer in scope

**5. Proposed layer structure**
Specify the target layer structure: what each layer covers and roughly where its boundary falls. Name sections, not abstract principles.

### Mode A output

Present the plan in chat as direct markdown — headings, tables, and bullet points rendered normally. Do not wrap the plan in a code fence. After presenting it, offer to save it to a file. Do not save automatically.

# Restructuring Plan: [document name]
Generated: [date]

## Canonical reference used
[path, or "none identified"]

## Document purpose
[One sentence.]

## Proposed layer structure
Layer 0 — Orientation: [what it covers]
Layer 1 — Conceptual model: [what it covers]
Layer 2 — Detail: [what it covers]
Layer 3 — Reference (if applicable): [what it covers]

## Ordered structural changes
1. [Specific move]
   Reason: [one sentence]

2. ...

## Forward references to resolve
For each: where it appears, what it references, how to fix it.

## Content to relocate out of this document
For each: what content, where it belongs, why.

---

## Mode B — Architecture Audit

Read all documents in the target directory. Do not read directories that begin with `.` or are named `scratch`. Do not read any file matching `architecture-plan-*.md` or `restructuring-plan-*.md` — these are output artifacts from previous runs, not part of the document corpus.

Diagnose the following:

**1. Document inventory**
For each document: its apparent purpose, its actual content, and whether those match.

**2. Foundational content audit (check this before boundary analysis)**
The canonical reference must answer three questions. Check whether it does, and if not, where those answers currently live:
- *Why does this research topic exist?* — the purpose, goals, or problem being solved
- *What decisions does this work support?* — the use cases, the practitioner actions that depend on the outputs
- *What is the stable model of the subject?* — definitions, invariants, foundational assumptions

If any of these are answered only in versioned, transitional, or planning documents — and not in the canonical reference — flag this as a **critical boundary violation**. This is the most important finding Mode B can produce. A use case or design driver that lives only in a versioned document is at risk of being lost or fragmented as the project evolves.

**3. Boundary analysis**
Where is the boundary between documents blurry or wrong:
- Content in one document that belongs in another
- Content duplicated across documents
- Content present only in transitional or versioned documents that should be in the canonical reference
- Topics that should exist somewhere but do not

**4. Canonical reference coverage**
What is present in the canonical reference, what is missing that should be there, and what is there but belongs elsewhere.

**5. Transitional documents**
For each versioned or transitional document: is its content stable enough to integrate into the canonical reference, or is it appropriately separate?

### Mode B output

Present the plan in chat as direct markdown — headings, tables, and bullet points rendered normally. Do not wrap the plan in a code fence. After presenting it, offer to save it to a file. Do not save automatically.

# Architecture Plan: [directory name]
Generated: [date]

## Canonical reference used
[path and basis for inference, or "none identified"]

## Document inventory
| Document | Stated purpose | Actual content | Match? |
|---|---|---|---|

## Critical boundary violations
Foundational content (purpose, use cases, design drivers) that is absent from the canonical reference. Each entry: what is missing, where it currently lives, what is at risk. If none: state explicitly.

## Boundary problems
Non-critical boundary issues: description, affected documents, consequence of leaving it as-is.

## Content migration
1. Move [content description] from [source] to [destination]
   Reason: [one sentence]

2. ...

## Canonical reference gaps
- [Topic]: currently in [location] / currently missing entirely

## Recommended document structure after changes
[Which documents exist, what each covers, where the boundaries are.]

---

## Saving the plan

When the user asks to save the plan — whether immediately after the initial output or after a discussion that refined it — write the plan as it stands at that point in the conversation to a file. Use the version that reflects any corrections or additions from the discussion, not necessarily the first draft.

File paths:
- Mode A: `<document-parent-directory>/restructuring-plan-<document-basename>-<YYYY-MM-DD>.md`
- Mode B: `<directory>/architecture-plan-<YYYY-MM-DD>.md`

Use today's date. Do not read any existing file before writing — each save produces a new timestamped file and the Write tool can create new files directly.

---

## Constraints

- Do not make content decisions. If a section contains domain errors, note it as out of scope and move on.
- Do not rewrite prose. Specify moves, not replacements.
- Every instruction in the plan must be executable without a follow-up question. If you cannot make an instruction unambiguous, flag it as requiring owner input before execution.
- State all inferences explicitly — canonical reference identification, assumed document purpose, assumed audience.
- **Write the plan in the language the host's documents use** (check the target's `AGENTS.md`), not the chat's — English unless the corpus says otherwise. The plan is presented in chat and saved verbatim as a file in the corpus folder, so it follows the corpus's document language even when the conversation does not.
