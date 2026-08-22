---
name: tribunal
description: "Tribunal: a refutation gate between a batch of your claims and the owner. Packages the batch as a cold-safe dossier, hands it to a cold orchestrator that builds a bench of fresh-context reviewers briefed to refute, and relays their verdicts verbatim. Use after producing a batch of substantive claims — numbers, mechanisms, conclusions, designs — before they reach the owner or a durable record, and unconditionally when the owner signals distrust of a claim series. The reviewers' verdicts, not your confidence, are what reach the owner."
argument-hint: "[which claims] — default: the current session's undelivered claim batch"
disable-model-invocation: true
---

# Tribunal

You are the **defendant, not the judge**. The session that produced a batch of claims is the least trustworthy judge of it — sunk investment, framing, revision fatigue. Your part is mechanical: package, spawn, relay. You never construct the bench, never re-judge, never soften a verdict.

## Contract

- **Fire per batch, never per assertion:** a bench costs a few hundred k tokens and is justified per claim batch. For one or two claims, push back — "merge or wait for the batch" — unless the owner overrides. Falsifier: a bench spawned on a 1–2 claim batch with no override.
- **Invocation is spawn consent, nothing more:** the owner's invocation pre-answers the harness's confirmation prompt for spawning agents. It changes no other policy — reviewers inherit the session's execution grants; under a no-execution policy the orchestrator must build lenses that attack without running code, and says so in the bench plan.
- **Scope:** substantive claims. Not a prose or structure review, and not a substitute for the owner's judgement of what matters.

## Phase 1 — Dossier (forcing function)

No agent spawns until the dossier file exists (session scratchpad). Header: where the data lives, where the record corpus lives, which execution policy binds.

- **The batch is complete:** every undelivered substantive claim of the session, not a curated subset. Excluding one is stated in the header, with the reason. Falsifier: a claim delivered to the owner this session that appears in neither the dossier nor the exclusion list.

One block per claim:

- **Id + descriptive title** — cold-safe (no bare local ids, no undefined symbols) and neutral: the title names what was measured, never how well ("shift estimate from frame pairs", not "noise-consistent shift estimate").
- **The claim** — exactly as you would state it to the owner, with its number and units.
- **Method** — the production steps as bare facts: code paths, data paths, the parameter values the claim is quoted at, reductions applied. Checks that were run are listed the same way — a path and what it did, no adjectives.

**Provenance only** *(load-bearing)*: dossier blocks state how each claim was produced, never why it is right — no validation summaries, no confidence terms, no pre-rebuttals. Reviewers design their own attacks; the dossier hands them material, not directions. Falsifier: a dossier block arguing rightness instead of stating method.

## Phase 2 — Cold orchestrator

Spawn exactly **one fresh-context orchestrator** — a subagent able to spawn its own subagents (Claude Code: Agent tool, type `general-purpose`). Its brief is the dossier plus this section's procedure, verbatim — never your chat, never your view of the claims. **Cold brief** *(load-bearing)* — bench construction happens outside the producing session because distrust of that session is the point. Falsifier: an orchestrator or reviewer brief carrying producing-session reasoning, or a lens charge authored in the main session.

Orchestrator procedure:

1. **Classify each claim by how it could be wrong.** Exemplar failure families — an open menu; extend or replace by naming a new family: *unsupported certainty* (asserted, never measured); *aggregation collapse* (one number standing in for acknowledged structure or a distribution); *instrument blindness / method defect* (selection bias, circularity, confound, insufficient lever arm, parameter sensitivity); *provenance & record collision* (already recorded, already refuted, or colliding with better-provenanced material); *inference error* (control validity, effective sample size, independence, arithmetic); *completeness* (what the batch conspicuously fails to claim).
2. **Build one reviewer per dominant family present** — typically 2–4. Each lens charge names three things: the failure family it hunts, the attack method, and the primary evidence surface it must consult (producing code, raw data, record corpus, external knowledge). **Non-convergence** *(load-bearing)*: lens charges must differ in attack method or evidence surface. Two findings are duplicates iff they target the same claim, cite the same evidence artifacts, and a single correction would dissolve both. Falsifier: duplicate findings reported as corroboration — they are a bench-construction failure, reported as such beside the verdicts, which themselves stand.
3. **Match model tier to lens difficulty:** mid/high capability tier by default (Claude: Sonnet/Opus-class); top tier only with a named reason. No tier selection in the harness → session default.
4. **Spawn reviewers in parallel; aggregate without re-judging:** verdict per claim per lens; the headline verdict is the worst across lenses, with any cross-lens disagreement still listed as a finding in its own right; failed attacks preserved as failed; reviewer-built artifacts attributed to their producer. Return the synthesis plus the bench plan — which lenses, why, which tiers — so the owner can audit the construction.

**Standing orders to every reviewer** (relayed by the orchestrator, verbatim):

- **Refute by default:** a close call is "refuted". Precedence: this breaks ties only between *refuted* and *survives-weakened*; a demonstrated weakening that does not overturn the claim is *survives-weakened* — never rounded to either pole.
- **Look at the evidence in natural form** before accepting any model of it — images as images, tables as tables, text at the source.
- **Report failed attacks as failed attacks:** a survived attack is evidence; omitting it is not neutrality.
- **Return what you build:** a better estimator, measurement, or reading is output, not scrap.
- **You cannot ask questions:** what the dossier fails to provide is a finding against the dossier.
- **Verdict vocabulary** *(load-bearing)*: **refuted / survives-weakened / survives**. A discovered weakening must appear in the verdict, not only in prose — and it must be material: it changes the claim's number, scope, or downstream use. Immaterial caveats do not downgrade. Falsifier: a report whose material weakenings live in prose under pole verdicts, or whose middle verdicts carry only cosmetic caveats.

## Phase 3 — Relay (verbatim)

- Chat gets the verdict table and the bench plan **unedited — no reorder, no upgrade, no omitted failed attack**; each *survives-weakened* row carries its weakening in one line. The full orchestrator report goes to a scratchpad file, path named in chat. Falsifier: any difference between the orchestrator's verdicts and the relayed table.
- You may append a response, clearly separated below the relay: next probes, corrections you will make, what you accept. It never re-argues a verdict — re-arguing is re-judging relocated below the table. Falsifier: relay commentary defending a refuted claim.
- Adjudication is the owner's. A refuted claim does not reach a durable record; a survives-weakened claim reaches one only restated with its weakening.

## Degradations (portability)

The skill assumes no specific harness (Claude Code, OpenAI, Gemini, …); mechanisms above are generic, the Claude Code instantiation is the worked example. Where a mechanism is missing, take the named degradation and state it in the relay:

- **No nested spawning** → the orchestrator returns lens charges; the main session spawns them copy-paste verbatim and passes raw reviewer reports to a fresh aggregator agent (or relays them raw). The main session still authors nothing.
- **No tier selection** → session-default model.
- **No scratchpad** → dossier and report inline in chat, clearly fenced.

## Falsifiers index

1. **Batch guard** — a bench spawned on a 1–2 claim batch with no owner override.
2. **Batch completeness** — a claim delivered this session that is in neither the dossier nor the exclusion list.
3. **Provenance only** — a dossier block arguing rightness instead of stating method.
4. **Cold brief** — an orchestrator/reviewer brief carrying producing-session reasoning, or a main-session-authored lens charge.
5. **Non-convergence** — duplicate findings (same claim, same evidence artifacts, one correction dissolves both) reported as corroboration.
6. **Middle verdict** — material weakenings in prose under pole verdicts, or middle verdicts carrying only cosmetic caveats.
7. **Verbatim relay** — relayed verdicts differing from the orchestrator's, an omitted failed attack, or commentary defending a refuted claim.
