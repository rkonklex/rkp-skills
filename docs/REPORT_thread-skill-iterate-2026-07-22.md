# Report — thread skill: fourth Iterate pass (growth discipline; benchmarked)

**Date:** 2026-07-22
**Thread:** `/metaprompt-engineer` Iterate on `skills/thread/SKILL.md` + `skills/thread/LINT.md`,
driven by the fourth heavy field session on the confidential trial record: one session added
+319/−46 lines — ~150 of measured derivation into findings, an 87-line new finding, a 39-line
session-log entry — and a structural audit of the record found 57 % of it in findings with no
distinction between live and settled, plus a session log at 10 % of the file.
**Status:** closed — edits applied in the same change as this report.
**Outcome:** an economy charge added to the lint (benchmarked, zero false positives), an
owner-gated collapse-into-micro-article lifecycle rule (benchmarked old-vs-new on the executing
tier), and lifecycle clauses in the skeleton contract.

Origin tags: **[observed]** — quotable from eval outputs, the audits, or the diff ·
**[inferred]** — this session's diagnosis · **[speculation]** — a guess.

## Frame

Pass-3 falsifiers: the narration class stayed contained (owner: "the lint works in principle").
What fired instead was a gap no falsifier covered — an **orphan premise**: "cold-parse cost
outranks narrative continuity" bound nothing about size. Two sub-gaps [inferred]:

- **Flow** — the lint checked narration and cold-readability, not whether added words earn
  their keep (the owner's explicit ask).
- **Stock** — no lifecycle: nothing said when a finding stops being detailed or when detail
  leaves for a `REPORT_`; the structural audit named this "the missing collapse policy". The
  skill routed restructuring to `/structural-audit` but never said *when*.

Owner rulings that shaped the design (three plan-review rounds):

1. **No trim-audit skill** — `/structural-audit` file-mode already diagnoses stock bloat; the
   fix belongs upstream, in the keeper's own envelope.
2. **Collapse must be owner-gated** — the field session eagerly declared a line "settled";
   an auto-collapse rule would have compressed a finding the owner still wants live (pending
   new data). Decline books a `[dormant]` wake trigger, so the candidate signal stays truthful.
3. **The export is a micro-article, not an archive** — first design (append-only frozen
   evidence units) rejected: "a relocated session log — garbage to the human reader." The
   REPORT the thread outputs is background + reasoning + results + conclusions, a proof of
   work; written by the *concluding session*, while the reasoning is still in context — a later
   session cannot author the train of thought. Changing a report later is re-authoring it as
   one piece, never appending.
4. **Mid-campaign detail stays in the thread** — it is legitimate working state; the lint's
   over-grain class exempts findings and binds the log, tracker, and Status prose. Mass export
   happens once, at campaign conclusion, through the gate.
5. **Confidentiality boundary** — this repo is public; the host project is not. Benchmark
   material stayed in-session; this report carries counts only. Tier hint recorded: thread
   integrates run on opus, the lint on sonnet.

## Changes applied

1. **Contract block (skeleton)**: closed status-keyword set; owner-confirmed collapse-to-kernel
   with the story leaving for a `REPORT_`; session log = last three entries verbatim, older as
   phase digests. Dual-homed with the Integrate rule deliberately — the contract block is the
   record's machine-readable self-description, which the audit skills extract invariants from
   and `/apply-edit` executes against without `/thread` loaded.
2. **New Integrate rule "Collapse what settled — flag, owner decides"** *(load-bearing)*: the
   collapse flag and the article trigger are one checkpoint event; on confirm, article + kernels
   (Status, claim, cited numbers, link); on decline, a `[dormant]` wake trigger; log rolling is
   mechanical; what no lifecycle rule places books `/structural-audit`.
3. **"State authority only" recast** to include owner-confirmed lifecycle moves (else it would
   contradict rule 2).
4. **"Fresh eyes" recast** to run all `LINT.md` charges; run counts now live only in `LINT.md`
   (de-dup).
5. **"Tag what you add" recast**: compounds combine declared members only; evidence stamps
   legal; free-text qualifiers to the sentence (field audit found 7 wild tag forms).
6. **`LINT.md` restructured**: narration/cold charge byte-identical (its pass-3 benchmark
   stands); new economy charge — duplicate / over-grain (log, tracker, Status only) / no-claim,
   on added lines only. Recipe: 2× narration/cold + 1× economy, unioned.
7. **Registry sync**: README thread row + "How they fit together" line;
   `plugin.json`/`marketplace.json` untouched (set character unchanged).

## Benchmarks

### Collapse/article rule (opus — the tier that runs thread integrates; in-session synthetic
scenario, invented greenhouse domain)

Stage S1: integrate a yield that settles the F2+F4 cluster, checkpoint on "save this, we
continue tomorrow". Stage S2: owner has confirmed; produce article + collapsed record. [observed]

| Arm | S1 | S2 | Notes |
|---|---|---|---|
| V0 — pre-pass-4 rules | 0/2 pass | — | both integrate cleanly, neither flags the settled cluster — detail stays in the record indefinitely (the field failure, reproduced) |
| V1 — pass-4 rules | 3/3 pass | 2/2 pass | every S1 run flags the candidate, proposes article + kernels, and waits; S2 articles are genuine micro-articles with kernels keeping only cited numbers |

- The baseline validates the eval: V0 reproduces the field gap in sandbox. [observed]
- Wobble (1/3): one V1 run *offered* to write the article "next session, while the reasoning is
  fresh" — self-contradictory; both S2 runs, where confirm was actually given, wrote
  immediately. Wording shipped unchanged; falsifier armed instead. [observed]
- Deviation (1/2): one S2 run dropped the executed probe row from the tracker after collapse
  (outcome living in log + article). Arguably the more one-home-consistent end state — the
  economy lint flagged exactly such rows as duplicates in the field record. Booked as an open
  grain question for the owner, not a failure. [observed]
- Unprompted quality signals: correct origin-set fidelity (the record declares `[observed]`,
  not `[measured]` — one run adjusted its stamps accordingly); mechanical log-rolling executed;
  one run surfaced a cross-finding coupling as a peer note. [observed]

### Economy charge (sonnet, 3 replicates; the real session diff, read in place)

Scored against 7 violations the diff demonstrably contains and a list of content that must not
be flagged (kernels, stamps, terse claims, mid-campaign finding detail) — both judged in-session,
so the numbers are directional. Effort caveat: runs used default effort; the recipe says low.
[observed]

- Single-run recall 5/7, 4/7, 4/7; three-run union 6/7; two-run unions 6/7, 6/7, 5/7.
- **False positives 0 across 54 flags** — the noise-flood falsifier did not fire; the charge
  errs toward precision.
- 8 genuine violations found beyond those 7 (settled-state prose in Status, cross-section
  duplicate pairs both added by the same diff, tracker rows carrying figures homed nowhere, one
  no-claim process line) — routed to record cleanup, see Open.
- Systematic miss: the one orientation-line duplicate (top-of-file summary restating an assets
  entry) escaped all three runs — summary-shaped lines read as derived views, not
  restatements. [observed]
- Recipe shipped as 2× narration/cold + 1× economy. A second economy run would lift expected
  recall from ~4–5/7 to ~6/7 at ~100k tokens per run — the owner's dial. [inferred]

## Rejected

- **A `trim-audit` skill** — duplicates `/structural-audit` file-mode; the gap was the keeper's
  missing exit path, not a missing diagnoser.
- **Auto-collapse on tracker emptiness** — breaks "flag, don't decide"; the field session's
  eagerness to settle is exactly why the gate exists.
- **Append-only evidence-unit report** — rejected by the owner as a relocated session log; the
  micro-article model replaced it.
- **Editing the benchmarked narration/cold charge** — the economy check is a separate charge, so
  the pass-3 validation stands byte-identical.
- **Size budgets in the skeleton** (per-layer line targets) — unmeasurable across records of
  different scale; the lifecycle mechanism bounds growth instead.
- **Post-eval wording tweaks** for the two wobbles — small-n, the actions (vs offers) were
  correct; falsifiers armed instead of re-wording (anti-oscillation).

## Artifacts changed

- `skills/thread/SKILL.md`, `skills/thread/LINT.md` — edits above (+~17 lines on the skill).
- `README.md` — thread row, "How they fit together".
- This report.

## Open / deferred / not established

- **Economy scores are directional** — this pass judged its own scoring basis, and "earns its
  keep" is owner taste; a validated number needs the bar set by the owner.
- **Executed-row grain after collapse** — does a collapsed campaign's `[executed]` tracker row
  stay (skeleton as written) or leave (one-home reading)? Owner's call; skeleton unchanged
  this pass.
- **Effort mismatch** — economy runs used default effort against a low-effort recipe;
  re-measure at low effort before quoting the recall numbers as recipe performance.
  [speculation: direction of the effect unknown]
- **Field quotes in pass 1–3 reports** — public `docs/` reports quote confidential field
  material; owner to decide on a sweep.
- **The field record itself** — the structural-audit restructuring plan and the consistency
  audit's findings await owner adjudication and execute via `/apply-edit` on the host side;
  nothing there was touched this pass.
- **Lint finds not covered by existing cleanup routes** — of the violations the benchmark runs
  surfaced, the session-log over-grain falls to the new rolling policy and the assets/Status
  duplicates to the restructuring plan; three duplicate figure pairs between findings are
  covered by neither — fold them into the restructuring plan's execution or clean at the next
  checkpoint.

## Lessons (meta)

1. **Length problems are lifecycle problems.** [inferred] Three passes policed *how* text is
   written (narration, cold-safety); the record still grew without bound because nothing said
   when content *leaves*. A hygiene rule cannot substitute for an exit path.
2. **The archive shape is an owner-taste axis prose cannot guess.** [observed] The append-only
   evidence log was internally coherent and exactly wrong — "few heavy micro-articles" vs
   "frozen units" is a preference only the owner could state, and it inverted *when* export
   happens (campaign conclusion, not every checkpoint).
3. **Gate placement follows from observed agent bias.** [observed] Integrating agents are eager
   to declare lines settled (field session; V0 runs happily established everything). The gate
   sits where the bias is, not where the ceremony is cheapest.
4. **Benchmark at the field tier.** [observed] Pass-3's rule eval ran on the sonnet tier;
   the field runs thread on opus. This pass's rule numbers are opus numbers; the "V2 transfer"
   falsifier is now satisfied rather than latent.
5. **Zero false positives is the load-bearing lint property.** [inferred] Recall can be bought
   with replicates and unions; trust, once eroded by noise flags, cannot. A charge that misses
   an item per run but never cries wolf survives contact with a rubber-stamping writer.

## Reviewer checklist — falsifiers for pass 5

- **Collapse eagerness returns** — a checkpoint compresses or writes an article without the
  owner's confirm; the gate didn't transfer to the field.
- **Deferred article** — owner confirms a collapse and the article is booked for "a later
  session"; the this-session binding failed (armed by the 1/3 offer wobble).
- **No flag at a settled cluster** — a campaign concludes in the field and no candidate flag
  appears at that checkpoint; re-run the scenario eval before re-wording.
- **Report strata** — any `REPORT_` gains an appended log section or reads as layered
  additions; the re-authoring clause failed (the owner's named fear).
- **Silent deletion** — collapsed detail absent from both the article and the kernel.
- **Economy noise** — flags landing on kernels, stamps, terse claims, or mid-campaign finding
  detail; charge too broad, trust eroding.
- **Economy blindness in the field** — the owner still finds duplicate/no-claim additions the
  lint never flagged; check first whether they're of the orientation-line shape (known miss)
  before widening the charge.
- **Log rolling skipped** — more than three verbatim entries surviving a checkpoint.
