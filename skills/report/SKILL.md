---
description: "Write a durable REPORT_<topic>.md: a self-contained, dual-purpose record of a session's work — a human reference plus auditable input for an AI review of the analysis and decisions. Use when asked to capture a session for the historic record or for review."
argument-hint: "<topic> — what the report covers, e.g. /report handoff-skills-design"
---

You're writing a **report**: the durable, self-contained record of what a session did — any session that reached conclusions, whether design, investigation, or measurement/analysis. Unlike a handoff (which briefs the *next* session and is all pointers), a report looks **backward** and **stands alone**: a reader with neither this chat nor the source handoff can follow the work and audit the conclusion. It serves two readers:

- **Human** — what was done, decided, and why; a reference point to return to.
- **AI reviewer** — auditable input: each claim carries its basis, and the open judgment calls are listed so a reviewer can check whether the conclusions actually follow.

So surface your own weak points honestly — a report that hides a shaky claim fails its second reader.

## Setup
1. **Focus** from the argument — a short description of what the report covers; derive a kebab-case slug for `REPORT_<slug>.md` in the work's folder. If omitted, infer from context. If a report for this topic exists, update it rather than spawn a near-duplicate.
2. **Conform to the host's authoring contract; read it before you draft.** Read the destination folder's `AGENTS.md` (or parent's) and any authoring-rules doc it names (e.g. `AUTHORING.md`) **before writing a line** — the read gates the write, never draft-then-reconcile. Conform at the **document level**: the language the corpus's documents use (not the chat's), its citation/anchor style (e.g. explicit `{#id}` anchors over `file:line`), and any code-context notation rules. The report keeps its own genre and structure. Absent a stated contract, match what existing corpus documents do; with no corpus, default to English.
3. **Never write into `scratch/`.** If a thread's handoff or notes hold a running session-log, this report **supersedes and merges** it into the durable record.

## Tag claims by origin
Separate what you **observed** from what you **inferred** from what rests on **uncited expertise** or is a **guess**, so a reviewer can weigh each. Define the tags once near the top: **[observed]** (a source, an instruction, or this session's measurement — quotable and spot-checkable) · **[inferred]** (derived by logic/topology, not directly seen) · **[domain-knowledge]** (general expertise, uncited) · **[speculation]** (a guess). The tag states where a claim came from; how *settled* it is rides the Status field and the Open / deferred section, not the origin tag.

## Structure (adapt — not every section applies)
- **Title + header.** `# Report — <focus>`. Then: **Date** (absolute), **Thread** (+ source handoff, referenced not required), **Status** (`ongoing` / `parked` / `closed`), **Outcome** (one line), and a one-line **dual-purpose / self-contained** statement.
- **Frame.** What this session set out to settle.
- **What was done — approach & inputs.** The path taken; sources, tools, and code by path.
- **Findings / conclusions.** The results and what they mean, each tagged. One sub-section per question where it helps.
- **Decisions taken, with rationale.** What was decided and *why*; alternatives weighed and rejected.
- **Artifacts changed.** Files created / edited / deleted — the record, and for review. Include process misses and corrections honestly; both serve the audit.
- **Open / deferred / not established.** Risks, what stays out of scope (with pointers), what is not yet confirmed.
- **Reviewer checklist.** The claims and judgment calls to audit. For each: what to check, and what would overturn it. This is the report's audit spine — be your own harshest reader.

## Before saving
Could a reviewer with neither this chat nor the handoff follow the work and audit the conclusion? Is every non-obvious claim tagged by origin, with inferences and provisional points flagged, not dressed as fact? Does the reviewer checklist name the *real* weak points, not soft ones? Is Status defaulted down — `ongoing`/`parked` unless the session leaves nothing to do **and** the report is being committed? Dates absolute?

## If the session produced data or measurements
Layer these onto the backbone:
- **Tag instantiation:** a measured value is **[observed]**; a quantity derived from it (logic/topology, not directly measured) is **[inferred]**. A number still in flux is not a tag — mark it provisional in Status / Open and keep it in its canonical home.
- **Method & inputs:** capture conditions, and the directed computations that produced the numbers.
- **Evidence inline but reduced:** small result tables only — **never raw per-step/per-frame arrays** (a plot referenced as an image is fine).
- **Numbers integrity:** if a figure you need is not reliably in context, **get it from the owner rather than reconstruct it from memory** — the numbers are the audit basis, not impressions.
