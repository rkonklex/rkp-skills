# Report — lead-engineer skill: first Iterate pass (comment rent, table soundness, output surface, ratified-entry stop; benchmarked)

**Date:** 2026-07-23
**Thread:** `/metaprompt-engineer` Iterate on `skills/lead-engineer/SKILL.md`, driven by a host-side
`/citation` audit of one heavy build session: **7 fired falsifiers (1 repeated), 3 uncovered
violations, 8 user-flagged events, all accounted for**. The audit's material (quotes, ids, values)
stays with the host; this report carries classes and counts.
**Status:** closed — edits applied in the same change as this report.
**Outcome:** four rules recast or added, one renamed with a precedence tiebreaker, the comment-rent
check escalated from prose to a fresh-eyes `LINT.md` gate (two charges), seven `*(load-bearing)*`
markers added. The lint gate is validated (recall + precision benchmarked); the two tactical rules
could not be separated — the baseline caught the planted defect in every arm.

Origin tags: **[observed]** — quotable from the citation audit, the benchmark transcripts, or the
diff · **[inferred]** — this session's diagnosis · **[speculation]** — a guess.

## Frame

The artifact had never been through an Iterate pass; it carried **zero** `*(load-bearing)*`
markers, so the citation author derived the falsifier list from scratch. Ten findings collapsed
onto six causes, and five of the ten shared one [inferred]: *a rule that was correct, on-topic, and
fully operationalizable, with no moment where the agent checked its own output against the file.*

1. **Comment rent, repeated** (derails, cost two rework turns) — the build shipped comments
   restating their own identifiers; the correction was applied to the flagged lines, then the next
   code written carried the same defect, forcing an identical second correction. The rule existed
   ("a comment earns its place only by carrying a non-obvious contract"); what was missing was a
   home for a mid-build correction to persist and a moment to check. Diagnosis [inferred]:
   **unmeasurable criteria** ("non-obvious" resolves toward writing more) plus an **orphan premise**
   ("preferences stated once persist for the session" named a lifecycle no Ledger section
   implemented).
2. **Comment cut left bare siblings** (cosmetic) — fixing finding 1 *caused* this one: cutting
   comments left new fields bare among all-commented siblings. Diagnosis [inferred]: **priority
   ambiguity** — cut-the-comment and match-local-form both fired with no tiebreaker.
3. **Module constant where the file uses inline defaults; commit message shaped unlike the repo
   log** (low / uncovered) — "match the baseline" covered the first verbatim and said nothing about
   artifacts emitted *around* the code. Same root as finding 1: baseline never checked.
4. **Decision table shipped with a duplicated condition and three unreachable rows** (high) — two
   gate predicates written in different variables were the same predicate once reduced to a common
   quantity; the rule mandated *coverage* ("every input-state cell") and stopped, never *validity*.
5. **A ratified table entry, found false in build, was corrected in-build and disclosed after**
   (moderate-high) — "scope = the Ledger" governed forks the Ledger didn't cover and was silent on
   a covered entry being *wrong*. Honest disclosure read as compliance.
6. **Objection demoted to a footnote** (high) — the strongest objection to the agent's own
   direction existed but was filed as a verification step, not stated beside the proposal.
7. **Output surface inflated, and a proposed document scoped too narrowly** (uncovered) — new
   public entries (some algebraically redundant) and a new document were each handed over as a
   single take-it list, never as a fork with scope options.

## Changes applied

1. **Ledger rule recast** — the orphan premise "preferences stated once persist for the session"
   replaced in place by **"A correction the user makes mid-build is a Ledger entry, not a one-off
   fix"** *(load-bearing)*: written into Rejected as a category before resuming, held over every
   later line; a second identical correction in one session is the falsifier. → findings 1, 2
2. **New Tactical rule "Coverage is not soundness"** *(load-bearing)* — restate every decision-table
   row in one common quantity and check each is still reachable given the rows above. → finding 4
3. **New Tactical rule "The output surface is a fork too"** — what a plan adds (public entries,
   config keys, documents) is a decision with scope options, and each new entry states what it
   carries that no existing one does. One vector covers both halves of finding 7.
4. **"Earn the bite" given placement** *(load-bearing)* — the objection lands beside the proposal in
   its own words; a mechanism resting on an unread/unmeasured value *is* the objection, not a
   follow-up. → finding 6
5. **New Build rule "A ratified entry found false is a stop, not a fix"** *(load-bearing)* — worded
   so that correcting-then-disclosing in one turn is itself the breach, closing the read that let
   honest disclosure pass. → finding 5
6. **"Match the baseline" scope widened** *(load-bearing)* — "where constants and thresholds live",
   plus a clause binding artifacts emitted around the code (commit messages, sibling docs). →
   finding 3
7. **"Comments as a knowledge cache" renamed "Everything you add pays rent"** *(load-bearing)* — the
   tag now carries the delete-by-default vector; single-use constants folded in; a **"Baseline wins
   on form"** clause is the precedence tiebreaker finding 2 lacked. → findings 1, 2, 3
8. **New Build rule "Fresh eyes gate the finish"** *(load-bearing)* + **new `LINT.md`** — the pass's
   one escalation. Five of the ten findings are a correct rule with no checking moment, in a context
   blind to its own output; the mechanism is a fresh-context charge on the diff, copied from the
   thread skill's proven shape (self-contained charges, fixed counts, unioned flags, no-affordance
   fallback). Two charges: **rent** (restatement / narration / single-use constant, added lines
   only, with an explicit sibling-matched-comment exemption so it cannot eat rule 7's tiebreaker)
   and **baseline** (orphan construct / odd member out, every flag grounded in a quoted sibling).
9. **Registry sync** — README lead-engineer row gains the output surface, the re-ratification stop,
   and the lint gate; "How they fit together" line unchanged (the drafting-table pairing is
   unaffected). `plugin.json`/`marketplace.json` untouched (set character unchanged).

## Benchmarks

House discipline applied (pass-4/5 precedent): the baseline must reproduce the gap or the result is
about the eval; field tier (rules on the executing tier, lint on sonnet-class, low effort);
executors blind to arm and hypothesis. Fixtures were a neutral synthetic module (rail telemetry
reduction), never host code, so nothing leaked toward this public repo. [observed]

### Tier 1 — the lint charges (validated; the load-bearing mechanism)

A synthetic module in the shape the citation describes — every threshold an inline default, one
struct with every field commented, one-line docstrings, no module constants — plus a planted
feature-addition diff carrying, at known locations: a single-use module constant, three bare new
fields among commented siblings, a signature-restating docstring, two narrating comments, and two
foreign typing/aliasing forms. Deliberate **must-not-flag decoys**: a thin comment on a new field
whose siblings all carry comments (the rule-7 precedence probe), a rationale comment, a terse
legitimate docstring. Three replicates per charge, sonnet-class. [observed]

| Charge | Recall (per run) | False positives | Precedence decoy |
|---|---|---|---|
| Rent | **4/4 all three runs** | **0** across all runs | survived — never flagged |
| Baseline | **3/3 core all three runs**, every flag sibling-grounded | 0 ungrounded | survived — never flagged |

- **Recall saturates at one run** for both charges; the union at 2–3 buys insurance, not lift.
  [observed] This set the recipe counts directly (rent 2, baseline 1) rather than by guess.
- **The precedence decoy held.** No run flagged the thin-but-sibling-matched comment — the rule-7
  tiebreaker and the charge's exemption clause agree, so escalation did not reintroduce finding 2.
  [observed]
- **One baseline run drifted** into general design review and flagged two items outside the charge
  (a dead duplicate helper, a redundant boolean field). Both were **true defects in the fixture**,
  not charge noise — diagnosed by fixing the fixture and re-running: the drift vanished, the 3/3
  core held, and the wording shipped unchanged (anti-oscillation). [observed]

**Precision — the load-bearing lint property.** Both charges were run against a real,
owner-*accepted* diff (host-side, read-only): every flag on accepted code is by construction a
false positive. [observed]

- **Rent charge: near-silent** — one run returned NO FLAGS, one surfaced a single borderline
  restatement. The precision bar holds. [observed]
- **Baseline charge: chattier** — 2–4 flags per run, *every one grounded in a quoted sibling*, and
  several genuinely defensible (a bare verdict field among commented siblings — the exact finding-2
  shape; a unit-tag convention broken in one catalog entry). **Zero ungrounded flags.** [observed]
  The charge errs toward grounded-surfacing, which is its design — it reports "N for your judgment",
  it does not auto-fix — but it does not hit a clean zero on accepted code. Recipe answer: the
  chattier charge runs **once**, bounding adjudication load. [inferred]

### Tier 2 — the two tactical rules (unvalidated; baseline did not fail)

Rule "Coverage is not soundness" and rule "A ratified entry found false is a stop" each got a
V0-vs-V1 arm (V0 = shipped skill, V1 = as above), opus, on a task carrying an algebraic-identity
collapse of the finding-4 shape. Both were **unvalidated — the baseline passed**. [observed]

- **Every arm caught the collapse.** All six tactical runs (V0 and V1) reduced the gate conditions
  to a common quantity, found the identity, and surfaced it as unbuildable-as-stated. Detection sat
  at ceiling in both arms. [observed]
- **Every build-mode arm honored "stop, not fix."** On a *ratified* plan carrying the same defect,
  all four runs (V0 and V1) refused to ship a silent correction: V1 stopped before writing the
  defective function and cited the rule by name; V0 implemented the plan verbatim, caught the defect
  in its own validation step, and surfaced it without patching. Neither reproduced the field's
  fix-and-disclose behavior. [observed]
- **Why the baseline passed:** the planted defect was a clean algebraic identity between quantities
  *defined in the task prompt itself*; the field defect was spread across a plan and discovered only
  mid-build. The synthetic trap was catchable by the reduction the rule prescribes, so the current
  executing tier did it unprompted. This is pass-5's lesson exactly — a blatant trap measures
  skimming, and a baseline that passes is a result about the eval. [inferred] Reporting either arm
  as "V1 holds 3/3" would convert a broken instrument into false validation; both rules ship marked
  **unvalidated**, resting on diagnosis.
- **What V1 did change was framing**, not detection: V1 produced explicit per-row reachability
  tables and cited the stop-rule verbatim, where V0 reached the same verdict ad hoc. A framing
  signal, not the checking signal — the same split pass-5 saw between its rule-1 arms. [observed]

## Rejected

- **Re-wording the two tactical rules after the null benchmark** — small-n, and the actions were
  correct in every arm; falsifiers armed instead of re-wording (anti-oscillation).
- **Cutting "Primitives first"** — a no-op candidate (never cited in either the live audit or the
  consumed one), but cutting on suspicion is the oscillation Iterate forbids, and this pass already
  carries one mechanism-sized change. Left in, flagged, deferred to a dedicated arm.
- **Plan v1's "Read the file back before you finish"** — the pass's first draft answered the five
  no-checking-moment findings with a self-review by the writing context. Cut: a read-back performed
  by the context that wrote the code is writer discipline wearing a checklist, the same class of
  wish that failed in the field. Replaced by the fresh-context lint gate. [inferred]
- **Folding findings 5 and 7 onto existing rules** — each is a genuine scope gap (a covered entry
  being wrong; the size of the surface a decision creates), not a rewording of "scope = the Ledger"
  or the fork map. New rules, not stretched old ones.

## Artifacts changed

- `skills/lead-engineer/SKILL.md` — edits above (92 → 125 lines; frontmatter, preamble, and the
  two-modes section untouched).
- `skills/lead-engineer/LINT.md` — new, two charges, counts benchmarked.
- `README.md` — lead-engineer row.
- This report.

## Open / deferred / not established

- **Both tactical rules are unvalidated** — the synthetic trap was too transparent for the executing
  tier. A discriminating scenario needs the defect spread across a multi-part plan, not stated in
  the task, so the reduction is not free. Until then they rest on diagnosis.
- **The baseline charge does not hit zero false positives on accepted code** — it surfaces grounded,
  often-defensible style flags. Bounded to one run; whether "grounded but debatable" flags erode
  trust in the field is the first thing the next citation should check.
- **The lint gate has no field checkpoint yet** — Tier 1 is synthetic; the real test is the next
  `/lead-engineer` build followed by a `/citation` against it.
- **"Fresh eyes" no-affordance fallback is untested** — the benchmark always had subagents; the
  self-lint-in-a-separate-pass branch was never exercised.
- **Effort caveat inherited from the thread benchmarks** — lint runs used default effort; the recipe
  says low. Re-measure at low effort before quoting the recall numbers as recipe performance.
- **"Primitives first" no-op** — still zero citations; run the dedicated arm or cut next pass.

## Lessons (meta)

1. **Five findings, one cause: a correct rule with no checking moment.** [inferred] The fix was not
   five stronger wordings but one mechanism — and the mechanism cannot live in the context that
   wrote the code. A read-back by the author is writer discipline; the gate is a fresh context.
2. **An escalation replaces a rule, it does not join it.** [inferred] Plan v1 added a read-back rule
   *and* kept the prose rules; the delivered pass cut the read-back for the lint gate, so the check
   has exactly one home. Additive-default is a failure mode of the repair, not only of the target.
3. **Zero false positives is the load-bearing lint property — and it is charge-specific.** [observed]
   The rent charge earns it; the baseline charge trades it for grounded recall. Reporting one number
   for "the lint" would have hidden that the two charges sit at different points on the precision
   curve, and hence deserve different run counts.
4. **A blatant trap measures skimming, not the rule.** [observed] Both tactical arms caught a defect
   the current tier catches unprompted, because the trap was stated in the task. Trap subtlety has
   to match the field failure, or the baseline passes and the arm proves nothing.
5. **The absence of load-bearing markers is itself a finding.** [inferred] An artifact that never
   marks its load-bearing rules makes every downstream audit re-derive the falsifier list; adding
   the markers is zero net lines and hands the next `/citation` its checklist.

## Reviewer checklist — falsifiers for pass 2

- **Mid-build correction not banked** — a second identical style/preference correction in one
  session, or a correction applied to flagged lines only and reverting in the next file written.
- **Table soundness returns** — a ratified decision table ships with two rows reducing to the same
  quantity, or a row unreachable given those above.
- **Output surface handed over flat** — new public entries or a new document presented as one list;
  the owner has to ask "can any be cut?".
- **Objection demoted** — the strongest objection appears only as a verification step or follow-up;
  or a mechanism rests on an unread value with that dependency unnamed at the point of proposal.
- **Fix-and-disclose returns** — a ratified entry corrected inside the build and disclosed
  afterward, *including* an honest, accurate disclosure. (Live: Tier 2 could not test it — the field
  is the first real test.)
- **Baseline breach around the code** — a commit message or sibling doc lands shaped unlike its
  repo/file neighbours.
- **Rent breach** — a comment restating its identifier, or a single-use parameter-default constant,
  reaches a commit.
- **Precedence breach** — a comment cut leaves bare members among annotated siblings (the finding-2
  shape returning), meaning "Baseline wins on form" did not bite.
- **Lint skipped or theater** — a build reported done with no lint line; or "lint: clean" reported
  over several builds with no subagent actually run, or run without the diff.
- **Lint noise in the field** — flags on owner-accepted code, on sibling-matching comments, or on
  general style with no quoted sibling; the baseline charge's grounded-surfacing tipping into noise.
- **Lint blindness** — the owner still finds restated comments or orphan constants the charge never
  flagged.
- **"Primitives first" still a no-op** — zero citations after another field session.
