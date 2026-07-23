# Report — thread skill: fifth Iterate pass (resume grounding, panel integrity, tag lint, blast-radius sweep)

**Date:** 2026-07-23
**Thread:** `/metaprompt-engineer` Iterate on `skills/thread/SKILL.md` + `skills/thread/LINT.md`,
driven by the fifth heavy field session. Evidence: a host-side CITATION audit of one integration
session — 3 fired falsifiers (1 repeated), 1 uncovered violation, 1 positive pattern the owner
flagged for retention. The audit's material (quotes, ids, values) stays with the host; this
report carries classes and counts.
**Status:** closed — edits applied in the same change as this report.
**Outcome:** resume recast around carried-vs-settled, a fixed-counts clause on the lint panel,
a benchmarked malformed-tag lint class, an ids-with-titles chat rule, and an owner-designed
blast-radius sweep around checkpoints. Three of the five rules separated their arms on the
field tier; the fixed-counts clause could not be tested because its baseline never failed.

Origin tags: **[observed]** — quotable from the citation audit, the benchmark outputs, or the
diff · **[inferred]** — this session's diagnosis.

## Frame

None of pass-4's reviewer-checklist falsifiers fired: the collapse gate, log rolling,
derived-view sync, and report re-authoring all held in the field — the citation's compliance
side confirms each. [observed] What fired was older machinery, plus one gap:

1. **Carried claims asserted as fact** (derails, repeated) — the opening resume summary
   presented the record's carried claims as settled; the owner corrected two. Diagnosis
   [inferred]: **priority ambiguity** (the declare step's "what is settled (you will not
   relitigate it)" primes assertion, while Boundaries says "input to verify, not authority" —
   no tiebreaker at the moment of the summary) plus a **wish without forcing function**
   ("re-open and quote the source" had no bite). The owner's meta-note — a good overall
   impression possibly resting on catching mistakes immediately — names exactly this: the
   derailing class was owner-caught, not skill-prevented.
2. **Lint panel under-run** (moderate) — the agent self-authorized a "proportional panel" on a
   small diff, running one narration/cold agent instead of two. Diagnosis [inferred]: the
   recipe stated counts but not their fixedness — an escape hatch left open by what the rule
   didn't say.
3. **Malformed origin tag survived to commit** (cosmetic) — a free-text qualifier inside the
   brackets, against an explicit format rule. Verdict: **prose won't fix this** — the rule
   existed and was violated; no lint charge owned tag format, so the gate is the mechanism.
4. **Bare ids in chat** (uncovered) — summaries referenced findings by bare id; the owner
   couldn't read them without the record open. The cold-safe rules govern the record; chat
   prose was unaddressed.
5. **Positive pattern** (owner-flagged) — an owner-initiated post-integration question: what
   are the consequences, the blast radius, of what was just integrated? Two of its lines fed
   back into the record. The owner asked to automate it around checkpoints.

## Changes applied

1. **Resume recast** — the declare paragraph now splits settled *decisions* (not relitigated)
   from carried *claims*; new rule **"Carried claims are readings, not facts"** *(load-bearing)*:
   no quote from the source, no building on the claim; a claim presented to the owner unmarked
   as carried has been asserted, not reported.
2. **`LINT.md` recipe** — counts fixed, a small diff does not shrink the panel. One home for
   the clause (the recipe); SKILL.md's pointer untouched.
3. **`LINT.md` economy charge, class (d) malformed tag** — a bracketed tag not built from the
   record's declared set; compounds of declared members and evidence stamps explicitly legal.
   The benchmarked narration/cold charge stays byte-identical. Benchmark below.
4. **Work rule "Ids travel with titles"** — a finding or probe named in chat carries its
   title; the owner reads chat without the record open.
5. **Integrate rule "Sweep the blast radius — pose, owner decides"** *(load-bearing)* — a
   checkpoint integrating a substantive new or corrected finding books a consequences sweep:
   offered before the checkpoint, posed right after the save if not taken there; the sweep
   never blocks the save. Owner-designed (before/after split), with two refinements accepted
   in review: mechanical checkpoints pose no sweep, and the mandate is to *pose*, not to run —
   the owner may wave it off, the hosting discipline does the thinking.
6. **Registry sync** — SKILL.md's fresh-eyes enumeration gains malformed tags; README thread
   row gains the sweep. `plugin.json`/`marketplace.json` untouched (set character unchanged).

## Benchmark A — rules 1, 4, 5 (opus, the field tier; synthetic record)

Two arms differing only by this pass's deltas: **V0** = the pre-pass-5 wording, **V1** = as
shipped. Scenario: resume a synthetic multi-session record and pull its rank-1 tracker item,
which can only be computed by building on two carried claims — both contradicted by the data
files the record cites. Three opus executors per arm, blind to the arm and to the hypothesis;
scoring by six separate opus judges, one per transcript, blind to arm, on quoted evidence.
[observed]

| Measure | V0 | V1 |
|---|---|---|
| Carried claims in the opening paragraph | asserted 1, mixed 2, marked 0 | **marked 3/3** |
| Findings named with the record's own titles | own paraphrase 2, sometimes 1 | **record title 2, sometimes 1** |
| Blast-radius sweep offered | **0/3** | **3/3** |
| Source re-opened and quoted before building | 3/3 | 3/3 |
| Planted contradictions caught | 2/2 in all runs | 2/2 in all runs |

- **Rule 1 moved the framing, not the checking.** Re-verification was at ceiling in both arms —
  the old rule already got the sources opened. What V1 changed is whether carried claims reach
  the owner *marked as carried*: V0 opened with "settled, I won't touch it" and corrected
  itself a section later; V1 opened by naming them as the previous session's reading. One V1
  run declared as settled only the parts that survived re-checking — the vocabulary split
  working as designed. [observed]
- **The ceiling is an eval artifact.** The planted contradictions were blatant and the data
  sat in two small files; the field failure had neither property. Read the checking result as
  "not reproduced here", not "cannot recur". [inferred]
- **Sweep separation is the cleanest signal** and it was unplanned — the scenario was built for
  rule 1. One judge scored a V0 fresh-eyes-lint mention as a sweep; on the strict reading (the
  lint is a different mechanism, and the judge on another V0 transcript rejected the same
  quote) V0 is 0/3. [observed]
- **One planted trap was not a real contradiction** — a temperature-sensitivity note outside
  the range the record actually claims. Three runs reasoned this correctly and declined to
  flag it; scored as an eval design error, not a miss. [observed]

## Benchmark B — rule 2 (fixed counts): no discriminating power

Scenario: a checkpoint whose whole session change is a two-sentence addition — the field
trigger for the self-authorized "proportional panel" — with the agent asked to state the lint
panel it will run. Three arms × 3 opus runs: **V0**, **V1**, and **V2** (this pass's clause
absent *and* the detailed benchmark note cut, i.e. the weakest wording of the three).

**All nine runs declared the full 2+1 panel; several volunteered "a small diff does not shrink
the panel" unprompted.** The baseline never failed, so the scenario cannot separate the arms
and **rule 2 is unvalidated** — neither supported nor refuted. [observed]

Two things the run did show. The V0 runs justified the count by citing the *detailed*
benchmark note ("run count, model tier, input mode measured together") — the line this pass
cut; V2 shows the count surviving that cut anyway, so the cut is not a regression on this
evidence. [observed] And the field failure evidently needs conditions this scenario lacks — a
long session, accumulated context, no prompt pointing at the recipe. [speculation]

## Benchmark C — class (d) on the real field diff

The malformed instance survived into the field session's closing commit, giving a natural
test case with one known target. Extended charge, 3 replicates, sonnet-class, host-side and
read-only. [observed]

- **Recall 3/3** on the known malformed tag; every run also proposed a declared-member fix.
- **False positives 0** — no legal compound, evidence stamp, or plain declared tag flagged.
- **(a)–(c) regression: none observed** — 5–7 flags per run, all of the established shapes
  (duplicate, over-grain, no-claim), none on kernels, stamps, or terse claims. The residual
  (a)–(c) flags are host-record cleanup candidates, handed to the owner in-session.
- Effort caveat inherited from pass-4: runs used default effort; the recipe says low.

## Rejected

- **Any change for the large finding rewrite** — accounted, not a breach: the contract
  mandates rewriting a falsified claim to current state; no renumbering, no layer reshaping.
- **Any change for draft-stage narration/duplicates** — the lint gate caught them pre-commit;
  the mechanism working as designed is not a finding against it.
- **A proportionality dial for the panel** — the run count is the owner's dial, set in the
  recipe, not the session's judgment call.
- **Sweep at every checkpoint** — the question wears out; the trigger is substantive finding
  changes only.
- **Mandatory sweep execution** — mandatory *posing* keeps "flag, don't decide" and the
  not-a-thinking-discipline boundary intact.
- **Tag-format check in the narration/cold charge** — its pass-3 benchmark stands
  byte-identical; the economy charge (provisional) took the class.

## Artifacts changed

- `skills/thread/SKILL.md` (+~14 lines), `skills/thread/LINT.md` — edits above.
- `README.md` — thread row.
- This report.

## Open / deferred / not established

- **Rule 2 is unvalidated** — benchmark B's baseline never failed, so the scenario has no
  discriminating power. A valid test needs the field conditions (long session, accumulated
  context, no prompt pointing at the recipe); until then the clause rests on diagnosis alone.
- **Rule 1's checking half is untested** — benchmark A separated the arms on framing only;
  re-verification was at ceiling in both. A discriminating scenario needs a subtle
  contradiction in a corpus too large to skim.
- **The sweep rule has no field checkpoint yet** — benchmark A's 3/3-vs-0/3 is synthetic, and
  the trigger-scoping judgment (which checkpoints are "substantive") is owner taste.
- **(d) benchmark is single-instance** — one known target in one real diff; recall beyond
  the free-text-qualifier shape (undeclared members, ratings) is untested.
- **Effort mismatch persists** — both economy benchmarks (pass-4 and this one) ran at default
  effort against a low-effort recipe.
- **Residual (a)–(c) flags on the host record** — await owner adjudication host-side.

## Lessons (meta)

1. **A "settled" vocabulary at resume primes assertion.** [inferred] The fix was not more
   emphasis on the verify rule but splitting the vocabulary: decision-state ("settled") and
   claim-state ("carried") are different words, so the summary can't blur them.
2. **An agent escapes through what a rule doesn't say.** [observed] Stated counts without
   stated fixedness invited a self-granted proportionality exception. Closing an escape hatch
   is a wording job on the rule's silence, not its emphasis.
3. **Format rules without a format check ride on writer discipline.** [observed] The cosmetic
   class survived precisely because no charge owned it; the gate, not the rule, is what scales.
4. **Positive patterns are Iterate evidence too.** [observed] The citation recorded an
   owner-initiated question worth automating; a violations-only audit would have lost the
   pass's largest behavioral addition.
5. **A baseline that passes is a result about the eval, not the rule.** [observed] Benchmark B
   was built to reproduce a real field failure and could not; reporting it as "rule 2 holds
   3/3" would have converted a broken instrument into false validation. Pass-4's V0-reproduces-
   the-gap check is the discipline — run it before believing any arm.
6. **Blatant traps measure the wrong thing.** [inferred] Benchmark A's contradictions were
   catchable by skimming two small files, so the checking behavior sat at ceiling in both arms
   and only the *framing* separated them. Trap subtlety has to match the failure being tested.

## Reviewer checklist — falsifiers for pass 6

- **Carried claim asserted again** — an opening summary states a record claim as fact and the
  owner corrects it; the vocabulary split didn't bite.
- **Quote theater** — sources quoted ritually for claims never built on, or a token quote
  pasted while the claim is used unverified; the forcing function satisfied in letter only.
- **Proportionality returns** — any wording ("small diff", "targeted run", "focused panel")
  that shrinks the recipe counts. This one is live: benchmark B could not test it, so the
  field is the first real test.
- **(d) noise** — malformed-tag flags on legal compounds or evidence stamps in the field.
- **(d) blindness** — a wild tag form reaches a commit again despite the charge running.
- **Sweep skipped** — a checkpoint integrating a substantive finding closes with no sweep
  posed before or after.
- **Sweep wear-out** — sweeps posed at mechanical checkpoints, or the owner waving them off
  as a matter of course; the trigger is too broad.
- **Bare ids return** — a chat summary again names findings or probes by id alone.
