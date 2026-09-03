# Report — structural-audit: full rebuild (grounded, benchmarked)

**Date:** 2026-09-02
**Thread:** `/metaprompt-engineer` Rebuild on `skills/structural-audit/SKILL.md`, driven by the
owner's verdict that the skill "can only pigeonhole any document into a four-level structure"
while its name and description promise a diagnosis.
**Status:** closed — rebuild applied in the same change as this report.
**Outcome:** one contract-driven procedure replacing two template-driven modes; a seven-class
defect vocabulary grounded in 94 field findings and a literature scan; 9/9 benchmark runs clean
on every observable; eight Iterate candidates recorded.

Origin tags: **[observed]** — quotable from agent outputs, the diff, or counts ·
**[inferred]** — this session's diagnosis · **[speculation]** — a guess.

## Frame

The skill had one instrument: a hard-coded `orientation → conceptual model → detail →
reference` skeleton with four output slots. Every document got sorted into it, so the "audit"
was a fixed classification. The one recorded field use (a work record, see the thread-skill
reports) needed a lifecycle diagnosis — settled material in live space — which the skeleton
cannot express. [observed]

Failure modes named in the diagnosis [inferred]: orphan premise (the description promises
"readability and layering" and "placement and boundaries"; no rule diagnoses either);
unmeasurable criteria in template shape; layer conflict with the consumer (`/apply-edit` treats
the plan as an unverified brief; each move carried only "Reason: one sentence"); scope
schizophrenia between the two modes; dead mode flags; negation blindness ("do not make content
decisions", no positive form); no adjudication step, no anti-manufacture rule, no falsifiers,
no origin tags. Kept on merit: the foundational-content check, now the High member of class 1.

Owner rulings: ground the defect set in experiments and literature, not in a pick — two of the
owner's corpora served read-only (a research corpus with its own authoring rules and a
~2400-line work record; an operations corpus of printed runbooks in a second language with
mirror copies); the artifact takes the house prefix, `AUDIT_structure-<topic>.md`; corpus
material stays in-session, this report carries classes and counts only.

## Changes applied

1. **One procedure, scope from the argument.** File → the document is the subject, its corpus
   the placement reference; directory → the corpus is the subject. Mode flags cut; `--canonical`
   kept.
2. **Contract harvest** *(load-bearing)* replaces the template: the document's own declaration
   (purpose, reader, grain, conventions, read order, skeleton block), then the corpus role table
   and host rules, then generic principles only where both are silent — each line tagged by
   origin. Genre changes what the contract looks like, never the classes.
3. **Section ledger** *(load-bearing)*: promise, kinds carried, size share, reader, home per
   contract, first-use vs definition, stock state, other homes. Read-list honesty: a finding on
   an unread file is the falsifier.
4. **Two-pass detection** *(load-bearing)*: generic signals produce candidates; the contract
   turns a candidate into a finding, sets severity, and can veto. A veto list guards against
   manufactured findings.
5. **Seven classes, each with a remediation verb** — the tiebreaker for overlaps: misplacement
   (move) · contract breach (retitle / re-scope / mark) · grain and proportion (split /
   condense) · dependency order (reorder / co-locate / signpost) · duplication (merge / link) ·
   stock rot (retire / archive / collapse / split) · orphan or empty home (home / create /
   delete).
6. **Finding bar:** location + contract line (quoted or tagged `[inferred]`) + one observable
   signal; severity High / Low; "where the structure fits its contract, say so."
7. **Report:** contract used · findings index with stable `S#` handles · sound structure · move
   plan grouped by verb, each move with evidence and origin tag, owner decisions marked,
   anchors to preserve per site, keep-despite-appearance, out-of-scope observations.
8. **Positive scope line:** a host authoring rule licenses a finding only when the fix is one
   of the seven verbs; notation, indentation and wording stay with `/apply-edit`.
9. **Registry sync:** README row and pipeline line; plugin descriptions unchanged. 171 → 125
   lines.

## Benchmarks

### Grounding experiment (defect set)

Three opus surveys classified every structural defect a cold reader hits against the seven
draft classes, plus OTHER; one sonnet agent scanned the literature (ROT content audits,
Diátaxis/DITA, information architecture, documentation-issue taxonomies, Wikipedia
maintenance criteria, ISO 29148, Zettelkasten atomicity, Carroll minimalism, heading-grammar
style rules). [observed]

| Survey | Findings | Classes fired | OTHER | Note |
|---|---|---|---|---|
| research corpus, canonical set | 21 | 7/7 | 0 | classes 4 and 7 never fired alone |
| research corpus, in-progress layer | 34 | 7/7 | 2 | record: 59 % findings, 8 % live state |
| ops corpus, runbooks + mirrors | 39 | 7/7 | 4 | class 1 overlapped five others |
| literature | — | 6 supported, 1 thinner (class 4) | 2 candidates | fixed templates documented to fail |

All eight OTHER and literature candidates folded into the seven by widening a definition:
dangling anchor / unfilled slot → class 7 (inverse polarity); maintainer apparatus in the
reader's path, audience seam, unbacked convention, broken formatting rule → class 2 (declared
reader / declared convention); disproportion and non-atomicity → class 3. Document size, which
the old format could not report, lives in classes 3 and 6. [inferred]

Three surveys independently reported the same split: **generic principles find the candidate;
the document's own contract decides whether it is a finding and at what severity.** Every
class-1 finding was contract-only. The veto list came from the surveys' "what is fine" lists:
newest-first order in a record, command-before-explanation in a card, copies declared
standalone / derived / photographs, superseded material inside a declared in-progress record,
size asymmetry proportionate to role. [observed]

### Baseline (current skill, verbatim, opus, n=1 per genre)

- Runbook: the four-layer skeleton was emitted; the agent's own meta note called the reference
  layer a misfit for a printed card and named two defects the format had no slot for — document
  size and drifted duplication across a sibling pair. [observed]
- Playbook (the template's home genre): the layer analysis "mostly describes what exists"; the
  run caught the order inversion and within-document duplication, missed a cross-document
  ownership call silently, and drifted into notation and indentation work. [observed]

### Rebuilt skill (opus, n=3 per genre, fresh context, identical prefix)

Observables, 0/1 per run: **A** no target skeleton not derived from the contract · **B** every
finding carries location + contract line + signal · **C** no veto-list item reported · **D**
anchors and cross-references listed per site · **E** no notation / indentation / wording moves ·
**F** (playbook only) catches the order inversion, the duplications, and the ownership call.

| Genre | Runs | A | B | C | D | E | Findings per run |
|---|---|---|---|---|---|---|---|
| printed runbook (~900 lines) | 3 | 3/3 | 3/3 | 3/3 | 3/3 | 3/3 | 10–17 |
| research playbook (~475 lines) | 3 | 3/3 | 3/3 | 3/3 | 3/3 | 3/3 | 11–16 |
| work record (~2400 lines) | 3 | 3/3 | 3/3 | 3/3 | 3/3 | 3/3 | 9–14 |

F on the playbook: order 3/3, duplications 3/3, ownership 0/3 — each run cited the corpus
index's "concepts primer" role for the document as sanctioning the copy, an adjudication left
to the owner rather than a miss. [observed]

Signals beyond the scored observables [observed]: two record runs verified the record's
address index mechanically before judging (44/44 rows, 434/434 tags); the record runs fired
class 6 zero times where the survey had found five cases, each mapping to a contract
protection or a booked exit path the runs cited — a veto working as written, booked as a watch
item; 7/9 runs invented a "Medium" severity with one convergent definition (a host rule
breached, drift risk, no reader harm today); 2/3 runbook runs reported in the chat language;
three runs independently asked for a move-plan slot for prerequisites in another file. Per
run: 134–213k tokens, 7–11 minutes.

## Rejected

- **A genre template library.** The failure being rebuilt away from; the literature documents
  fixed templates failing once content does not fit their slots. Genre appears only as
  examples of what a contract looks like.
- **An eighth class.** Every candidate folded by widening a definition; class-by-verb keeps
  the set closed.
- **Findings-only output with the plan on a later accept.** Two rounds every time; the
  single-run plan binding only for accepted findings keeps the gate and the convenience.
- **Post-benchmark wording changes.** Nine clean runs; the wobbles are booked as Iterate
  candidates with falsifiers, not patched (anti-oscillation).

## Artifacts changed

- `skills/structural-audit/SKILL.md` — rebuilt (171 → 125 lines).
- `README.md` — catalog row, "How they fit together" line.
- This report.

## Open / deferred

- **Iterate candidates** (rewrites unless marked +): (i) add Medium to the severity scale with
  the runs' definition; (ii) language: the audit takes the language the corpus declares for
  *records*; (iii) "read every file you cite in full" → "every file you make a finding on";
  (iv) ledger columns constant across a document collapse to one line; (v) the ownership call
  under a declared primer role is named as an owner decision; (vi+) move-plan entry gains a
  "prerequisites elsewhere" line — the one addition, gated by `PROVE.md`; (vii) a missing
  notation row is class 7, not notation (runs split 2:1); (viii) a settled unit with a *dormant*
  exit path — this audit's flag or the thread skill's collapse gate?
- **Directory scope untested** — all nine runs were file scope. **Baseline n=1 per genre** —
  the rebuild is a shorter rewrite, ungated under `PROVE.md`; the baseline runs are diagnosis
  evidence, not an arm. **Literature gap** — no primary source on lab-notebook / runbook
  structure was reached.

## Lessons (meta)

1. **Ground the vocabulary before writing the rule.** [inferred] The seven classes survived
   three genres and the literature because they were tested against 94 real defects first.
2. **Generic finds, contract decides.** [observed] Three independent surveys reached the same
   split; it became the two-pass shape and the veto list. Generic signals alone flag a
   declared photograph as the corpus's worst drift.
3. **Runs converge on what a rule lacks.** [observed] Seven of nine invented the same severity
   band; three asked for the same missing slot. A convergent invention is a rule the model
   already wants.
4. **A veto that silences a class is not a miss until a case escapes it.** [inferred] Zero
   class-6 findings on the record looked like blindness; each survey case had a contract
   protection the runs cited.

## Reviewer checklist — falsifiers for the next pass

- **Skeleton returns** — a run proposes a target layer structure not derived from a harvested
  contract line, or the same skeleton for two genres.
- **Bare finding** — a finding without location, contract line or signal; a finding citing no
  ledger row; a finding on a file absent from the read list.
- **Veto breach** — newest-first order, command-first order, a declared standalone / derived /
  photograph copy, or role-proportionate size reported as a finding.
- **Manufactured findings** — a run with zero findings and no sound-structure paragraph, or a
  clean document given a move plan.
- **Scope drift** — a move whose fix is notation, indentation or wording.
- **Blind move** — a move-plan entry without evidence or origin tag; a renumbering without a
  per-site anchor list; a move that rewrites prose.
- **Silent ownership call** — a copy sanctioned or condemned with no owner-decision marker
  where the contract declares a primer or teaching role (armed by 0/3).
- **Rot escapes the veto** — a settled unit with no exit path at all reported as sound
  (distinct from the dormant-exit-path watch item).
- **Unasked save** — an `AUDIT_*` file written without an offer; a prior audit read as corpus.
