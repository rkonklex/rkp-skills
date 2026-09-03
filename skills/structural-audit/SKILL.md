---
name: structural-audit
description: "Audit where content lives and how it is organized for its reader — one document, or a directory as a corpus. Judges against the document's own contract (declared purpose, reader, rules), never a fixed template; reports seven defect classes with evidence as an indexed findings table plus an evidence-carrying move plan the owner accepts and /apply-edit executes. Not truth (epistemic-audit), not agreement (consistency-audit), not prose."
argument-hint: "<path> — a file (the document is the subject, its corpus the placement reference) or a directory (the corpus is the subject); e.g. /structural-audit docs/operations.md. Flag: --canonical <path> names the corpus's canonical reference explicitly."
disable-model-invocation: true
---

# Structural Audit

**Objective:** Report where content sits in the wrong place, at the wrong grain, in the wrong
order, in two homes, past its life, or with no home — judged against the document's own
contract, never against a shape this skill carries. The owner adjudicates; `/apply-edit`
executes the moves he accepts.

**Inputs:** $ARGUMENTS = a file or a directory. File → the document is the subject and its
corpus the placement reference. Directory → the corpus is the subject: placement between
documents, role honoring, duplication across files. `--canonical <path>` names the canonical
reference; otherwise infer it from the host's rules and the corpus index, and state the
inference.

## Scope
- **IN:** the seven defect classes below, within a document and between documents.
- **OUT — log a one-line "Out-of-scope observation" and move on:** whether a claim is true
  (epistemic-audit); whether documents agree on a value (consistency-audit); wording, notation,
  indentation, prose quality — these stay with `/apply-edit` even where a host authoring rule
  governs them. A host rule licenses a finding here only when the fix is one of the seven verbs.

## Phase 1 — Contract harvest *(load-bearing)*
Before judging anything, write down what the structure should be and where that came from:
- **The document's own declaration:** purpose, reader, grain ("commands to transcribe only"),
  conventions, read order, a contents list, a skeleton or contract block. Quote each line.
- **The corpus's role table and the host's rules:** the index or README role assignments, the
  authoring rules already in context or the authoring doc they name (read it; do not
  enumerate rulebooks), the canonical reference's declared scope.
- **Generic principles, only where both are silent:** one home per fact; the reader meets a
  definition before its use; a section carries the kind its heading names; detail
  proportionate to role. Tag these `[domain-knowledge]`.

Tag every contract line `[observed]` (quoted) or `[inferred]` (with the inference stated).
Genre changes what the contract looks like, never the classes: a work record's contract is its
skeleton and its live/settled split; a spec's, its depth layers; a playbook's, its task order;
a printed card's, jump access and grain; a handoff is transitional by declaration, so settled
results inside it are misplaced by construction. *Falsifier:* a finding whose expected shape
cites no contract line and no tagged inference; one target skeleton proposed for two
documents of different genres.

## Phase 2 — Section ledger *(load-bearing)*
One row per section — per document too, at directory scope: `heading and what it promises ·
what the body carries (kinds) · lines and share · declared vs actual reader · home per contract
· first use of a term or claim vs where it is defined or grounded · stock state (live /
settled / superseded / historical) · other homes of the same content`. Read every file you cite
in full. At directory scope list files and sizes first; if the corpus exceeds what you can
read whole, name the files not read and scope back with the owner — never audit an unread
file. *Falsifier:* a finding citing no ledger row, or on a file absent from the read list.

## Phase 3 — Detection *(load-bearing; two passes)*
**Pass A — candidates from generic signals** over the ledger: size share per heading level and
sibling ratio · kinds per section · heading grammar vs body form (infinitive = task, noun
phrase = concept) · count promised vs carried · a stated order vs the heading order ·
first-use-to-definition distance · a qualifier's distance from what it qualifies ·
near-verbatim repeats within and across files · superseded / for-now markers and
declared-settled units in live tiers · tail blocks, catch-all headings, empty anchors and
slots · index completeness.

**Pass B — the contract adjudicates:** a candidate becomes a finding only when a contract line
makes it one, and the contract sets severity. The contract also **vetoes** — these are not
findings: newest-first order in a record; command-before-explanation in a card read under
pressure; a copy the corpus declares standalone, derived, or a photograph; superseded material
inside a declared in-progress record (the missing exit path is the defect, not the material);
size asymmetry proportionate to role; a maintainer section shipped where the rulebook does not
travel.

Classes — one finding per signal; when two fit, the class is the one whose fix the finding
implies:

| # | Class | What it names | Verb |
|---|---|---|---|
| 1 | Misplacement | content homed in a section or document other than the one its declared role gives it; High when settled or foundational material (purpose, use cases, the stable model, measured results) lives only in a transitional document | move |
| 2 | Contract breach | a declared promise the body does not honor — a heading, contents list or section intro; a declared reader; a declared convention | retitle / re-scope / mark |
| 3 | Grain and proportion | detail or size out of proportion with the section's role and siblings; several kinds under one heading; rationale inside a do-this section | split / condense |
| 4 | Dependency order | the reader needs something placed later or too far away — a definition, a prerequisite, a warning, a qualifier; reader dependency, not chronology | reorder / co-locate / signpost |
| 5 | Duplication | one fact with two homes; the offender is the copy whose container does not own the fact | merge / link |
| 6 | Stock rot | settled, superseded or historical material in live space with no marker in place or no exit path; growth past what the structure carries | retire / archive / collapse / split |
| 7 | Orphan or empty home | content no section owns; or a home with no content — an anchor whose content dissolved, a field never filled | home / create / delete the empty home |

**The bar for a finding:** location (file § section) + the contract line it breaches, quoted or
tagged `[inferred]` + one observable signal (a quote of at most 15 words, a count, a size
share, a line distance). Any part missing → not a finding. **Severity:** High = a reader
acting on the document is misled or must read elsewhere first; Low = cosmetic. **No
manufactured findings:** where the structure fits its contract, say so — sound structure is
reported so the executor does not "fix" it. *Falsifier:* a finding missing one of the three
parts; a vetoed item reported as a finding; a run with zero findings and no sound-structure
paragraph.

## Phase 4 — Report
Direct markdown, in the host's document language, not the chat's; no code fence around it.
1. **Contract used** — the harvested lines with tags; the canonical reference and how it was
   identified; files read, and files not read.
2. **Findings index** — one row per finding, ordered by severity, nothing else ranked:
   `S# · class · severity · location · contract line · signal · verb`. Stable handles the owner
   triages ("accept S2, S5, S9").
3. **Sound structure** — one paragraph.
4. **Move plan** — one entry per finding, grouped by verb: `S# · from · to · what moves (by
   section or lines, never rewritten prose) · evidence (the finding's contract line and signal)
   · origin tag`. Executable by `/apply-edit` without a question, else marked **owner
   decision** with the options. Then three lists: **Anchors and cross-references to preserve
   or repoint** — every id and link a move touches, per site (a renumbering lists each site);
   **Keep despite appearance** — negative results, sanctioned copies, historical material the
   contract protects; **Out-of-scope observations**.

The plan binds only for findings the owner accepts. It is an edit brief: `/apply-edit`
re-derives its claims, so every entry carries what re-derivation needs. Specify moves, never
replacement prose.

## Saving
Offer once to save; never save unasked. Path: `<target directory>/AUDIT_structure-<topic>.md`,
topic = the document basename or the directory name; if it exists, add a numeric suffix.
Never read prior `AUDIT_*` files as corpus content.

## Constraints
- **Flag, do not decide:** name both homes and the contract line; the owner picks which. Only
  accepted findings reach `/apply-edit`, never the raw list.
- **This skill prescribes.** It judges a corpus; it does not orient a reader to an unfamiliar
  one, and it does not check truth or agreement — route those to their audits.
- **Load-bearing rules carry their falsifiers inline;** a `/citation` pass checks them.
