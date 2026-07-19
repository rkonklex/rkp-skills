# Report — thread skill: third Iterate pass (change-narration; benchmarked lint)

**Date:** 2026-07-19 (second pass this date; suffix b)
**Thread:** `/metaprompt-engineer` Iterate on `skills/thread/SKILL.md`, driven by the third
heavy field session on the confidential trial record: a probe-redo integrate whose working-tree
diff was saturated with "old state + update" prose in live sections, despite the session
correctly acknowledging the checkpoint in chat.
**Status:** closed — edits applied to `skills/thread/SKILL.md` in the same change as this report.
**Outcome:** one evaluated rule recast (corrections → corrected *or updated*, plus a cold-reader
test; picked from four benchmarked variants), one new mechanism rule (fresh-eyes lint agent at
every checkpoint; model/effort/input benchmarked), one sweep cut (Cold-safe self-re-read tail —
the failed self-check the lint replaces). First pass to *measure* candidate wordings before
committing them.
**Self-contained:** benchmark and eval artifacts live in the invoking session only; everything
load-bearing is restated here. Git history holds the *what*; this report holds the *why*.

Origin tags: **[observed]** — quotable from the field diff, the pre-edit SKILL.md, or a
benchmark/eval output · **[inferred]** — this session's diagnosis · **[speculation]** — a guess.

## Frame

The pass-2 correction falsifier ("any live section carries correction narrative … instead of
current-state text") fired again — in a third surface form. Form history [observed]:

1. Pass 1: a prepended correcting sentence next to the stale claim (judged a session problem).
2. Pass 2: "Correction: … withdrawn" blocks (rule recast to "reads as if written today";
   that form has not recurred).
3. This pass: supersede/update narration woven into claims — six sites of one shape: re-measured
   counts announced as superseding the earlier ones, which stayed on the page beside them; a
   retracted claim narrated as retracted against "the earlier reading"; "still X, now for a
   different reason"; an old evidence scope restated with the wider re-confirmation in
   parentheses; a corpus-growth sentence; and a re-resolved metric described against the layout
   it replaced.

The owner's meta-question at invocation: is further rule refinement still the right path, or is
a feedback-loop mechanism needed that offloads quasi-mechanical checks, leaving only judgment
calls? Direction set at plan review: benchmark model+effort combos for the checking agent, try
instruction variants steering toward minimal, and (on the owner's challenge) do not assume the
checker must be denied the diff — measure it.

## Findings

### Two roots, one per fix

- **Scope gap (prose-fixable).** [observed] The pre-edit rule binds "a **corrected** claim";
  most field violations were *updates* — the evidence base grew, counts were re-measured.
  A corpus-growth sentence is compliant under a literal reading. [inferred] The missing
  discriminator, drawn where every violation lived: a provenance stamp
  (`[measured, P6 2026-07-19]`) names evidence and stands; change-narration is informative only
  to a reader who remembers the old state. Test: does the sentence inform a reader who never saw
  it?
- **Missing affordance (not prose-fixable).** [inferred] "Reads as if written today" is a
  reader-stance property; the writer holds old state + new findings in context and cannot
  un-know them. The pre-edit self-check ("re-read this session's writes as the next session
  would", Cold-safe entries) asks the same context to simulate a cold reader — it knows what it
  meant, so it passes its own writes. Three passes of rule-sharpening failed with the rule
  loaded and mid-session acknowledged; each recast killed the last surface form and the
  generator survived. The check needs actually-fresh context, which the harness affords
  (subagent).

### Rule-variant eval (which wording changes behavior)

Four variants, each given to integrating agents (sonnet/medium — the typical executing tier)
with real field material: S1 = a finding paragraph stating a count over an old corpus scope +
the grown-corpus re-confirmation finding; S2 = a stability bullet carrying four per-item counts
+ the re-measurement finding whose own phrasing hands over the diachronic framing. Pass = output
neither retains old-state values nor narrates change. [observed]

| Variant | S1 | S2 | Notes |
|---|---|---|---|
| V0 — pre-edit rule | 2/2 | 0/4* | both S2 runs kept the old counts and bolted the new ones on |
| V1 — contract line widened ("corrected or updated … never old state plus what changed") | 2/2 | 0/2 | contract clause alone did not transfer |
| V2 — V1 + cold-reader test replacing the "Correction: …" ban-sentence | 2/2 | 5/6 | the only variant with clean S2 outputs |
| V3 — V2 + marker-word list (supersedes / retracted / re-measured / …) | 2/2 | 1/2 | markers bought nothing; one failure despite them |

*V0 S2 counted over the two direct replicates; V1's two failures share the mechanism.
V2's S2 cell was hardened with four extra replicates (n=6). Small n throughout — verdicts are
directional, and sharp only where cells are extreme (0/4 vs 5/6).

- **The eval is valid**: V0 reproduces the field failure class in sandbox. [observed]
- **The winner is V2** — smallest variant that passes; the behavior change rides on the
  cold-reader test sentence, not on the contract clause (V1) and not on marker enumeration
  (V3). [inferred]
- **Even V2 leaks ~1/6** on the hardest scenario — prose alone does not close the class; the
  lint is a needed net, not decoration. [observed]

### Lint benchmark (who checks, and with what input)

12 combos — {opus, sonnet, haiku} × {low, medium} × {file-only, file+diff} — each a
fresh-context agent given the record (and in diff mode the session diff), charged to flag
change-narration and cold-unreadable sentences in the touched sections. Scored against a
hand-built ground truth from the real field diff: 11 must-catch violations, 9 borderline
(either verdict acceptable), a must-not-flag list (Session log, provenance stamps, skeleton
status vocabulary). [observed]

- **Diff-mode beats file-only at every tier**, most strongly on cheap models (haiku/low 5→9,
  haiku/medium 7→10, of 11) and it halves noise flags. The owner's challenge to the "no diff"
  assumption was correct: seeing the old→new relation helps catch bolted-on constructions (an
  old evidence scope restated with the wider re-confirmation in parentheses) that read merely
  odd to a cold reader.
  The feared failure mode (old state visible → linter under-flags) did not materialize.
- **No combo guarantees full recall in one run.** sonnet/low/diff over three replicates: 11/11,
  7/11, 9/11. Misses concentrate on the provenance-adjacent phrasings (corpus growth, a
  re-measurement restated at three redundant sites) — exactly the borderline-flavored
  ones. opus single runs reach 10–11/11 at ~5× the cost, with FP on skeleton status vocabulary.
- **Two cheap runs, flags unioned, beat one large run**: measured unions of sonnet/low/diff
  pairs — 11/11, 11/11, 9/11 — at ~2/5 the cost of one opus run. This recipe is what the rule
  encodes. [observed + inferred]
- Both stale internal contradictions planted by the field session (an evidence line still calling
  an executed re-run pending; a status line still naming the pre-growth corpus scope) were found
  by most combos — the cold class works. [observed]

### Field cleanup (host project, executed alongside)

The 11 must-catch sites plus the two stale references were rewritten to current state in the
field record (stories already lived in its Session log), its contract block synced to the new
skeleton wording, and a session-log entry added. Post-cleanup verification ran the production
recipe (2 × sonnet/low/diff, union): every narration flag gone, and both runs converged on a
single genuine cold find — an undefined shorthand used six times in one finding and defined
nowhere in the file — escalated to the owner rather than filled with an invented definition. First use of
the checkpoint protocol produced exactly its intended division of labor: mechanical fixes done,
one judgment call up. Record left uncommitted per the owner's working-set convention.

## Decisions — changes applied to `skills/thread/SKILL.md`

Each change traces to the evidence above; architecture untouched (Iterate is surgical).
Net +7 lines on a 150-line file, +5 of them the mechanism rule.

1. **Correction rule recast to the evaluated V2** *(load-bearing)*: "A corrected **or updated**
   claim reads as if written today", the "Correction: … withdrawn" ban-sentence replaced by the
   cold-reader test + the provenance-stamp exemption. ← scope gap; variant eval.
2. **Contract line synced** (the rule's other home): "a corrected or updated claim is rewritten
   to current state where it stands, never old state plus what changed". Kept although V1 alone
   failed — the contract block is the only layer that binds sessions editing without `/thread`
   loaded; it needs the current wording even if the behavior change rides on the rule.
   ← layer placement.
3. **New Integrate rule `Fresh eyes gate the checkpoint`** *(load-bearing)*: fresh-context
   agent, fed the record and the session's diff, never the chat; two cheap low-effort runs
   unioned; fix or escalate; verdict reported with the checkpoint ("lint: clean" / "N fixed,
   M for your judgment"); no-subagent fallback named. ← missing affordance; lint benchmark.
4. **Sweep cut in Cold-safe entries**: the self-re-read tail ("re-read this session's writes as
   the next session would…") replaced by a pointer to the lint — it was the same-context
   self-check that failed three times; enforcement now has one home. ← additive-default guard.

**Rejected:** V3's marker-word list (no measured benefit; +2 lines); a regex/hook lint
(brittle — the markers are also legitimate probe names, and the violations are semantic);
strengthening the self-check wording (same-context blindness is the root, not salience);
pinning an exact model name in the rule (harness-dependent — "cheap low-effort" states the
benchmarked tier without a phantom affordance).

## Artifacts changed

- `skills/thread/SKILL.md` — edits above.
- This report.
- Field cleanup in the host project's record (uncommitted, owner's working set).
- Registry sync check: no add/rename/remove, frontmatter `description` unchanged, set character
  unchanged → `README.md`, `plugin.json`, `marketplace.json` untouched per the repo contract.

## Open / deferred / not established

- **Small-n benchmark.** [speculation] Most combos ran once; sonnet/low/diff variance (7–11/11)
  suggests other single-run numbers carry similar spread. The directional claims (diff > file;
  no single-run guarantee; union helps) rest on the extreme cells and should survive; per-combo
  rankings should not be quoted as precise.
- **Legacy narration debt in the field record.** The lint surfaced pre-existing violations from
  before this session (a finding narrating that corrections landed after its first cut, a method
  described against the one it replaced, a header narrating the file's own conversion, a status
  line narrating a redesign) — out of this
  cleanup's scope, cheap to sweep in a future session; they may resurface as lint flags
  run-to-run until swept or explicitly sanctioned.
- **Lint cost in long sessions.** Two ~80k-token runs per checkpoint; a many-checkpoint session
  multiplies this. If it stings, scope the lint's read to touched sections — untested.
- **Pass-2 falsifiers stay armed** where not superseded: checkpoint-scoping held this session
  (the field session recognized the checkpoint); tag-under-`[owner]` did not recur.

## Lessons (meta)

1. **Prose has a measurable behavior-change ceiling.** [inferred] Three recasts of one rule
   failing on the same class was the signal to stop asking "how to say it stronger" and test
   whether any wording transfers. The eval localized the behavior change to a single sentence —
   the cold-reader test, read at write time; an equivalent contract-layer clause transferred
   nothing (V1: 0/2), markers added nothing (V3). And the ceiling is real: the winning wording
   still leaks ~1/6 — the remainder belongs to a mechanism, not a stronger adjective.
2. **Reader-stance invariants cannot be self-checked.** [inferred] A writer cannot un-know its
   own context, so "re-read as the next session would" was a wish, not a check. This
   generalizes to every cold-safety contract on artifact-writing skills: enforcement needs
   actually-fresh context, with judgment calls escalated to the owner.
3. **A-priori mechanism intuitions lost to measurement, twice.** [observed] "No diff for the
   linter" — diff-mode won every tier and the feared under-flagging never appeared. "One good
   run suffices" — single-run variance (7–11/11) dominated the design; unioned cheap runs beat
   one large. Both reversals came from the owner challenging an unevidenced design assertion;
   each challenge cost one benchmark axis to settle.
4. **Updates are sneakier than corrections because the inputs arrive diachronic.** [inferred]
   Findings naturally come phrased as change ("the earlier counts were artifacts…"); the
   record contract is a translation task, not transcription. Corrections announce themselves;
   updates masquerade as additive facts — which is why surface-form bans kept losing.
5. **Ground truth from field evidence turns wording disputes into evals.** [inferred] The
   labeled set built from the real diff made rule variants and checker combos scoreable; the
   V0 baseline validated the eval's discriminating power; the harness re-runs for pass 4.

## Reviewer checklist — falsifiers for pass 4

- **Gate skipped** — a checkpoint is presented with no lint verdict line.
- **Context leak** — the lint prompt carries session findings or chat content (the diff is
  sanctioned input per the benchmark; the chat never is).
- **Class survives** — change-narration outlives a checkpoint (lint missed it or its flag was
  waved through). Distinguish: missed → widen the charge; waved → the escalation protocol is
  toothless.
- **Noise flood** — the lint keeps flagging sanctioned vocabulary (skeleton status values,
  provenance stamps) and the writer starts rubber-stamping; spec too broad, trust erodes.
- **Mechanism wrong** — the owner still finds "old state + update" prose the lint never
  surfaced; then pass 4 re-litigates the mechanism design (input, run count, model tier), not
  the rule wording.
- **V2 transfer** — the eval ran on sonnet/medium; if the executing tier in the field differs
  and V0-style failures recur under V2, re-run the variant eval on the actual tier before
  touching the wording.
