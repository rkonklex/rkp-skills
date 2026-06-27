---
description: "Detect contradictions, drift, and rule breaches within and between research documents. Reports findings as flags for the owner to adjudicate — does not pick a winner."
argument-hint: "directory or explicit list of source documents. Flags: --fix (propose edits, mechanical only) · --focus restructuring"
disable-model-invocation: true
---

# Consistency Audit

**Objective:** Report where the documents disagree — within a document or
between documents — as flags for the owner to adjudicate. This audit judges
*agreement of claims only*.

**Inputs:** $ARGUMENTS = a directory or explicit list of source documents.
Flags: `--fix` (propose edits, mechanical only) · `--focus restructuring`
(weight the move/rename/recompute classes).

## Scope (read before starting)
- **IN:** contradictions between/within docs; breaches of the corpus's own
  declared rules; broken or stale cross-references; divergence of a term,
  definition, formula, or number.
- **OUT — do not pursue:** whether a claim is *true* (epistemic audit) or
  whether content sits in the *right file* / reads well (structural audit).
  If you spot one, log it as a one-line "Out-of-scope observation" and move on.

## Phase 1 — Invariant harvest
Read any document that declares rules for the corpus (an index/conventions
section, AGENTS, a style guide). Extract every *checkable* rule as: `rule text
— source file#anchor`. Rule shapes to expect: "term defined once and reused",
"file X links inward only", "maturity of a part ≤ maturity of what it feeds",
"citations use a profile, not a bare name", "built work in spec, aspirations in
roadmap". If no rulebook exists, say so and proceed to Phase 2.

## Phase 2 — Ledger (build before judging anything)
Over all *source* documents, record one row per: definition · formula · numeric
value/threshold/constant · maturity tag · cross-reference — each as `{item,
verbatim value, file#anchor}`. This is your evidence base. **Every finding in
Phase 3 must cite ledger rows; a finding with no ledger entry is invalid.**

## Phase 3 — Detection (two separated passes)
- **Pass A — Invariant conformance:** for each harvested rule, find ledger rows
  that breach it. The finding names the breached rule.
- **Pass B — Free contradiction:** scan the ledger for collisions — two entries
  about the same thing whose values cannot both hold (two formulas for one
  quantity, two thresholds, a term defined two ways, an absolute claim vs its
  hedged twin).

Apply these classes across both passes: rename drift · dangling or auto-ID
cross-ref · orphaned stale duplicate · formula divergence · definitional drift ·
numeric/threshold collision · maturity-vs-content mismatch · invariant breach.
Under `--focus restructuring`, prioritise the first four.

## Phase 4 — Report

**The bar for a finding (load-bearing — apply ruthlessly):** either (a) two
verbatim quotes, each with its location, that cannot both be true; or (b) a
harvested rule plus a verbatim quote that breaches it. Differing wording,
differing level of detail, or a hunch is **not** a finding. If you cannot quote
both sides, drop it.

**Frozen layer:** treat `REPORT_*` / historical / superseded documents as
**link-targets only, never sources**. Divergence between a living doc and a
frozen one is expected and is never a finding — **except** when a living
document deep-links into a specific claim inside a frozen doc that is now false
(class: stale cross-ref). That single case is a finding.

**Adjudicate nothing — flag only.** For each finding give both sides. If the
corpus's own dependency rules imply which side is authoritative (e.g. a
canonical base document), name it — but do not pick a winner or edit. Under
`--fix`, apply only mechanical repairs (broken anchor, a surviving old name);
**before any edit, read the target folder's `AGENTS.md` and any authoring-rules
doc it names (e.g. `AUTHORING.md`)** — a mechanical anchor repair is still a
corpus edit and must follow the host's anchor/notation contract. List every
semantic contradiction for the owner unresolved even then — `--fix` is
mechanical-only and never resolves one. The owner adjudicates each; only a
finding he accepts goes to `/handoff-edit` (staged as a dossier for
`/apply-edit`), never the raw list.

**Format:** findings ordered by severity. Per finding —
`ID · class · severity · A: file#anchor "quote" · B: file#anchor "quote" ·
breached rule (Pass A only) · fix (only if --fix)`.
Severity: **High** = a contradiction a reader would act on, or a broken
committed cross-reference; **Low** = cosmetic drift. Close with a count by
class, then the "Out-of-scope observations" lines.
