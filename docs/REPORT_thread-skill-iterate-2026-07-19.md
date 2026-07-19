# Report — thread skill: second Iterate pass (mid-session checkpoints)

**Date:** 2026-07-19
**Thread:** `/metaprompt-engineer` Iterate on `skills/thread/SKILL.md`, driven by the second
field citation from a units-audit session on the same confidential external record as the
first pass.
**Status:** closed — edits applied to `skills/thread/SKILL.md` in the same change as this report.
**Outcome:** one root-cause recast (Integrate scoping: temporal phase → per-checkpoint
invariant), one overturned prior rejection (the correction rule, per its pre-registered overturn
condition), three sweep cuts; the four other fired rules deliberately untouched.
**Self-contained:** the citation is not committed here; everything load-bearing from it is
restated. Git history holds the *what*; this report holds the *why*.

Origin tags: **[observed]** — quotable from the citation or the pre-edit SKILL.md ·
**[inferred]** — this session's diagnosis · **[speculation]** — a guess.

## Frame

Second heavy field session on the same record produced a falsifier citation: 5 fired falsifiers
(3 repeated), 1 uncovered violation, 3 unsubstantiated flags (all accounted). The owner's
hypothesis at invocation: a mid-session state dump ("save what we settled, let's continue") is not
recognized as Integrate, because the skill pins Integrate to session end; and a direct
"Integrate" command might be read as *closing the envelope*, discharging the rules for the rest
of the session. The owner's governing model, stated at plan review: the skill binds
continuously, all session long, with checkpoints/snapshots along the way — the envelope is a
standing contract, not a phase sequence.

## Findings — what the evidence established

### The shared root (skill problem, fix applied)

- **All five fired falsifiers are Integrate rules.** [observed] Correction-as-narrative (×2),
  stale claims at secondary sites, inferences under `[owner]` tags (×4), duplicated facts (×2),
  derived views out of sync — every one a rule under the pre-edit heading
  "**Integrate** (before the session ends — the envelope is not closed until this runs)".
- **The firings happened on mid-session writes, with completion declared.** [observed] The
  citation's finding 5 states it outright: "Integrate formally binds at session end, but
  completion was declared with the views out of sync" — the agent twice presented integration as
  complete mid-session; the gap surfaced only after the owner asked whether the Integrate rules
  bind every update of the file.
- **Diagnosis: phantom affordance.** [inferred] "Session end" is not a discrete, observable
  event — after any write the session may stop or continue, and the agent cannot know which.
  Nine rules were gated on a non-event, so mid-session saves escaped them. One root explains all
  five firings; the owner's hypothesis confirmed.
- **Diagnosis: fused terminal state.** [inferred] "The envelope is not closed until this runs"
  makes Integrate the closer — a mid-session "integrate now" licenses the reading *envelope
  closed, rules discharged* (the owner's second concern). Integrate must be repeatable, and the
  envelope has no close ceremony at all: it simply stops receiving writes.

### The correction rule (prior rejection overturned)

- **Finding 1 — retraction narrative left in a live section, ×2.** [observed] Two consecutive
  edits to one finding used "Correction: … withdrawn" blocks at the claim site instead of restating current
  state, while (correctly) logging the story to the Session log; the owner intervened
  by quoting the skill's own rule back.
- **The first pass rejected a text change for the same rule** (FF1: a prepended correcting
  sentence next to the stale claim), calling it a session problem — and pre-registered the
  overturn condition: "overturned if a reasonable reading permits the observed prepend."
  [observed, from the 2026-07-18 report]
- **The condition is now met.** [inferred] The tag's own words — "Correction lands at the
  claim" — permit, even invite, the observed move: the agent literally landed a correction *at
  the claim*. The leading words prime the act of writing a correction, not the end state of a
  rewritten claim. Second firing, second distinct compliant-looking misreading → skill problem.

### Fired as compliance failures under the scoping bug (no text change)

- **Finding 2 — stale claims at secondary sites** (notation table, pseudocode comment).
  [inferred] Covered by the existing one-home + sync rules once they bind per checkpoint.
- **Finding 3 — four agent inferences under `[owner]` tags, two factually wrong.** [observed]
  The first pass's tag-default falsifier, fired. [inferred] The rule ("a claim you derived
  yourself breaks the default and carries its own tag") is precise; under the scoping bug,
  mid-session writes were thought unregulated. Re-armed per checkpoint; if it fires again
  post-fix, this rule needs its own forcing function.
- **Finding 4 — one measured value in three homes, a binning fix in two.** [observed] One-home rule
  precise; same scoping story.
- **Finding 5 — Status prose and a finding's rows not synced.** The direct evidence for the root cause
  (see above).

### Out of scope

- **U1 — a format parameter never measured despite recurring assumptions about it.** [observed]
  The citation itself notes no rule covers it: the skill scopes itself to record-keeping ("Not a
  thinking discipline"); the measurement obligation lives in the host's rules. The record-side
  damage — wrong decodes entering under `[owner]` tags — is finding 3. No change.
- **Three unsubstantiated flags** (prior session's tool quality, owner-supplied data overturning
  a chat-side decode, accidental revert). [observed] All accounted in the citation;
  none breaches the artifact.

## Decisions — changes applied to `skills/thread/SKILL.md`

Each change traces to the evidence above; architecture untouched (Iterate is surgical).

1. **Integrate stanza header recast** *(load-bearing)*: temporal phase → per-checkpoint
   invariant. "Checkpoint" chosen as the leading word — it recruits the prior of a consistent,
   resumable state, defining the event with no session-end vocabulary: presenting the record as
   updated is a checkpoint, a state the next session could cold-resume from, and any checkpoint
   may be the last; work in progress may be transiently inconsistent, a checkpoint may not; an
   integrate closes nothing — the contract stays on, the next write arms the next checkpoint.
   ← findings 1–5 shared root, owner hypothesis + governing model.
2. **Entry rule**: "integrate before the session ends" → "the envelope is on for the rest of the
   session … integrate at every checkpoint". ← same root.
3. **Envelope heading**: `resume → work → integrate` → `resume once, then work ⇄ integrate` —
   the linear chain taught the one-pass reading. ← same root.
4. **Correction rule recast** *(load-bearing)*: tag "Correction lands at the claim" → "A
   corrected claim reads as if written today"; the imperative now names the end state, and both
   observed misreadings are named in the ban (no "Correction: … withdrawn" blocks in live
   sections; never narrate the fixing outside the Session log). Body semantics unchanged.
   ← finding 1 ×2 + first pass's FF1, overturn condition met.
5. **Contract block synced**: "a correction lands at the claim it corrects" → "a corrected claim
   is rewritten to current state where it stands" — same rule's other home, kept in agreement.
   ← change 4; one home per fact.
6. **Sweep cuts**: the binding condition now lives once in the stanza header — "before closing,"
   cut from Cold-safe entries; "before closing" cut from Sync the derived views; "at close" →
   "at every checkpoint" in Paths resolve. ← changes 1–3; one home per fact.

**Rejected:** per-rule forcing functions for findings 2–4 (additive-default — the rules are
precise and the scoping recast re-arms them); cuts of the first pass's additions (one session
without a cold-safe or rejected-write firing is not no-op evidence — the standard the first
report applied to its plan item 7).

## Artifacts changed

- `skills/thread/SKILL.md` — edits above (~+2 net lines on a 145-line file).
- This report.
- Registry sync check: no add/rename/remove, frontmatter `description` unchanged, set character
  unchanged → `README.md`, `plugin.json`, `marketplace.json` untouched per the repo contract.

## Open / deferred / not established

- **The recast is unvalidated.** [speculation] No session has run under the checkpoint framing;
  the falsifiers below are the test.
- **"Checkpoint" strength untested.** [speculation] The word must beat the model's default
  deferral at the moment of a mid-session save; if the agent still defers, the leading word is
  too weak and needs strengthening, not a technique switch.
- **Tag-under-`[owner]` recurrence.** If finding 3's pattern fires again post-fix, the tag rule
  graduates from compliance failure to under-specified and needs its own forcing function
  (e.g., re-scan new owner-class content for derived claims at each checkpoint).
- **First pass's untested falsifiers stay armed:** rejected-write oscillation and cold-safe did
  not fire this session; still unvalidated, not vindicated.

## Reviewer checklist

- **The root-cause claim** — do all five firings really share the scoping bug? Sharpest doubt:
  finding 3 (tags are written at write time; nothing is "deferred"). Overturned if a post-fix
  session mistags under `[owner]` while otherwise honoring checkpoints — then finding 3 had its
  own cause and the triage was too parsimonious.
- **The FF1 overturn** — was the second firing genuinely a distinct compliant-looking
  misreading, or repeated non-compliance? Overturned if the recast rule fires again in the same
  "Correction:"-block form — then the tag was not the cause.
- **Checkpoint-scoping falsifier** — the agent presents the record as updated ("done", "fixed")
  while any Integrate invariant is unmet.
- **Always-on falsifier** — after an explicit mid-session integrate, a later write in the same
  session skips any invariant (contract treated as discharged).
- **Correction falsifier** — any live section carries correction narrative ("Correction:",
  "withdrawn", "previously") instead of current-state text.
