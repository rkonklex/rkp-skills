# PROVE.md — the arms a proposed addition must survive

**These counts are design plus one measured pass, not a settled benchmark.**
One controlled pass (opus-class agents, one scenario family, n=5 per arm):
without the gate, 2 of 5 runs shipped an unvalidated addition; with it, 0 of 5,
and the arms killed a plausible addition whose smallest variant measured as
useless-to-harmful. Record what each pass observes; revise these numbers on
evidence, and note here when a revision lands.

Recipe: fill `<TARGET>` (the artifact as it stands) and `<PROPOSAL>` (the
addition, verbatim). Each agent below runs fresh-context and receives only
those two plus its charge — never the proposing chat's reasoning.

1. **Adversary** (one run): argue `<PROPOSAL>` redundant — name the line in
   `<TARGET>` that already covers it; then construct the compliance path — how
   an agent obeys the proposal and still commits the failure it claims to
   stop. A landed redundancy kills the proposal before any arm runs.
2. **Scenario** — authored by the adversary, never the proposer: a task on
   which the failure has a real chance to occur, plus one binary observable
   two scorers would agree on. A scenario worded in the proposal's own
   vocabulary is invalid; so is one where the failure cannot occur.
3. **Arms** — same task prompt, differing only in the artifact text, at least
   3 runs each:
   - **none** — `<TARGET>` as-is. Necessity: the failure must occur here.
   - **smallest variant** — the adversary's minimal rewrite with the same
     claimed effect. Sufficiency and minimality: failure near zero; and if the
     variant suffices, ship the variant, never the full proposal.
   - **off-target probe** — `<TARGET>` plus proposal, on an unrelated task the
     artifact already handles. Benefit: no degradation.
4. **Emit beside the verdict:** each agent's exact prompt, the variant's full
   text, n per arm, and the counts. A verdict without these is unauditable.

Known instrument limit (measured, 10/10 null on a failure the field record
shows happening; corroborated 2026-09-01 by two more nulls — 3/3 and 3/3 no-
failure baselines on additions whose field failures were session-pressure or
over-cued-fixture cases): fresh-context arms cannot reproduce failures whose
mechanism is session pressure — sunk investment, revision fatigue, a long
chat's drift.
A null there means "wrong instrument", never "rule unnecessary"; such changes
ship unproven for the owner to accept, or as harness mechanisms rather than
prose.
