# Report — thread skill: first Iterate pass (post field-use)

**Date:** 2026-07-18
**Thread:** `/metaprompt-engineer` Iterate on `skills/thread/SKILL.md`, driven by field evidence
from the skill's first heavy deployment on a confidential external project's large research
record.
**Status:** closed — edits applied to `skills/thread/SKILL.md` in the same change as this report.
**Outcome:** 6 rule additions/recasts fixing 4 uncovered violations and 3 audit-found gaps; 4
evidence items rejected as session problems or no-ops.
**Self-contained:** the three source evaluation documents (a falsifier citation, a restructuring
plan, a consistency audit) are *not* committed; everything load-bearing from them is restated
here. Git history holds the *what*; this report holds the *why*.

Origin tags: **[observed]** — quotable from the source evaluations or the pre-edit SKILL.md ·
**[inferred]** — this session's diagnosis · **[speculation]** — a guess.

## Frame

The thread skill was pushed "to its limits and beyond" (owner's words) in one long external
session. Three evaluation artifacts came back:

1. **Falsifier citation** — audited the session transcript against the skill's own rules: 5 fired
   falsifiers (FF1–FF5, rule existed and was broken), 4 uncovered violations (UV1–UV4, no rule
   covered the behavior), 5 unsubstantiated flags (correctly no breach).
2. **Restructuring plan** — a structural audit of the record itself, ending in 7 "input for the
   thread skill" items (the plan itself ranked items 1–3 as high-value).
3. **Consistency audit (Part C)** — 4 meta-observations from auditing the record, plus one
   positive pattern to sanction.

The owner's brief: separate *session* problems (agent broke a clear rule) from *skill* problems
(rule missing or under-specified); fix only the latter; consider what the skill could do to catch
these failures earlier.

## Findings — what the evidence established

### Skill problems (gap confirmed, fix applied)

- **UV1 — entries not cold-readable (flagged ×4 in one session).** [observed] Freshly written
  record content depended on the writing session's chat context — undefined parameter names,
  shorthand meaningless to a future session. [inferred] Root cause: the skill *stated* the premise
  ("The file is the only memory across sessions") but no rule operationalized it — a wish without
  a forcing function. The biggest gap.
- **UV2 + FF3 — oscillation under correction.** [observed] When the owner rejected a
  record-keeping decision (a ~12-line spec dumped into a tracker item), the agent patched locally,
  then over-corrected: spun a ~10-line agreement off into its own NOTE file (fit one entry),
  then cut a rewrite below spec, losing a load-bearing qualifier. Convergence took 4+ rounds per
  issue; visible owner-trust damage. The citation states outright: "the skill has no rule for how
  to respond when the user rejects a record-keeping decision." [inferred] The envelope heading
  promised `resume → work → integrate` but the **Work** stanza did not exist — the mid-session
  phase had zero rules.
- **UV3 + UV4 — no entry hygiene.** [observed] Digressions, facts restated from other sections
  (which then desync on the next correction), and a term defined inline inside an evidence bullet
  instead of the notation section. No rule bound facts to one home.
- **FF2 — Planned-vs-tracker boundary undefined.** [observed] The skeleton listed both "Planned,
  not implemented" and tracker `[live]` items with no rule separating them; the field record
  duplicated four items across the two lists, and the spec-in-tracker dump (the UV2 trigger) had
  no stated correct home.
- **FF5 — tag semantics under section defaults.** [observed] An agent-derived (and factually
  wrong) claim sat inside an `[owner]`-tagged entry, inheriting owner provenance — in the exact
  entry future sessions are meant to trust without re-asking. Separately, the record had to
  replace the skill's example tag set wholesale with a domain one
  (`[owner]/[measured]/[computed]/[inference]/[ext]`) — correct, but nothing in the skill said the
  examples were replaceable, and the consistency audit noted the missing bridge to the host
  corpus's provenance classes at promotion time. [inferred] Classic example-overfit risk: a less
  confident session would treat the example set as fixed.
- **Derived-view drift beyond the Status table.** [observed] The audit found a corpus count stale
  in one finding after the evidence base grew (three sites disagreeing), a measured range stale
  against a later probe, and the same experiments ranked independently in two
  places. The old "sync the indexes" rule covered only the Status table.
- **Broken outgoing paths.** [observed] Six `.py` links broke when session tools moved to a
  `code/` subfolder; the whole Session-tools section was non-navigable for the next session.
  No integrity gate existed at envelope close.

### Session problems (rule was clear; agent broke it — no text change)

- **FF1 — correction appended instead of landing at the claim.** [observed] Told a component was
  still shipping, the agent prepended a correcting sentence and left "is retired" standing next
  to it. [inferred] "Fix the claim where it stands" is unambiguous and load-bearing; the falsifier
  fired and the audit caught it — the rule worked as designed. Adding text would be patching a
  compliance failure with prose.
- **Status-paragraph bloat (restructuring plan item 2).** [observed] The plan claimed the "one
  paragraph, no history" rule breaks at 15 findings. [inferred] Pushed back: the skeleton already
  said "the live forks, no history" — the 14-line settled-state recap violated the existing rule
  rather than exposing a missing one. Only a clarifying recast applied (settled state → index
  rows).
- **Unsubstantiated flags (5).** [observed] All correctly resolved in the field; one (agent
  holding a grounded `sin` quote under owner pushback until the owner retracted) is the
  re-grounding rule working exactly as intended.

### Rejected evidence items

- **Multi-line Grounding block (plan item 4).** [inferred] The skeleton is declared "floor, not a
  form"; growth is already licensed. Blessing it explicitly is bloat.
- **Reconciliation debt stamped at point of deviation (plan item 7).** [inferred] No-op: the field
  record did this unprompted, with no rule. A rule that buys no behavior change costs context for
  nothing.

## Decisions — changes applied to `skills/thread/SKILL.md`

Each change traces to the evidence above; anything untraceable was treated as oscillation and not
made. Architecture untouched (Iterate is surgical).

1. **New `**Work**` stanza** in the envelope, one rule: *a rejected write resets to purpose* —
   no patching at the point of rejection, no swinging to the opposite extreme; re-derive owner
   section / size / future reader and state the derivation before rewriting. *(load-bearing)*
   ← UV2, FF3.
2. **New Integrate rule `Cold-safe entries`** *(load-bearing)*: every entry reads without the
   session that wrote it; before closing, re-read the session's writes as the next session would.
   This is also the early-detection mechanism the owner asked for — the check runs at integrate,
   not at the next resume. ← UV1.
3. **New Integrate rule `One home per fact`**: one anchor per fact/number/definition, pointers
   elsewhere; new terms anchor in the notation section. ← UV3, UV4.
4. **Boundary defined in the skeleton comments**: Planned = unbuilt designs awaiting
   *implementation*; tracker = open questions awaiting *resolution*; specs/designs live in a
   finding, the tracker points. **Split move got a floor**: an agreement or spec that fits one
   entry never splits. ← FF2, FF3, plan item 3.
5. **Tag rules recast**: the contract now says tags come "from the set declared here", default set
   replaceable wholesale by the host's provenance vocabulary; section defaults
   (`[measured unless noted]`) sanctioned, with the exception spelled out — a claim the agent
   derived itself breaks the default and carries its own tag; Close's reconciliation checklist
   gains tag→provenance mappings. ← FF5, plan item 5, audit C-1, audit's positive pattern.
6. **`Sync the indexes` → `Sync the derived views`** (repeated numbers and ranks included;
   recompute, don't carry, any count whose evidence base changed) **+ new `Paths resolve` gate**
   (outgoing links/paths resolve at envelope close). ← plan item 6, audit C-2/C-3/C-4.
7. **Minor recasts**: Findings-map skeleton comment past ~10 findings (never renumber for reading
   order) ← plan item 1; Session-log entry "later additions merge into it, never extend it"
   ← FF4; Status comment "settled state lives in the index rows" ← plan item 2 (clarification
   only, see pushback above); host-conformance line gains "provenance vocabulary".

**Alternatives weighed:** folding the paths gate into the sync rule (rejected — different vector:
referential vs derived-view integrity); a hard line-cap on log entries (rejected — brittle;
merge-don't-extend targets the observed growth mechanism instead); a rule for FF1 (rejected — see
session problems).

## Artifacts changed

- `skills/thread/SKILL.md` — edits above (~15 net lines added on a 119-line file).
- This report.
- Registry sync check: no add/rename/remove, frontmatter `description` unchanged, set character
  unchanged → `README.md`, `plugin.json`, `marketplace.json` untouched per the repo contract.

## Open / deferred / not established

- **The new rules are unvalidated.** [speculation] They target the observed failures, but no
  session has run under them yet. The falsifier list below is the test.
- **File growth.** ~15 lines is the largest single-pass increase this skill has taken; the next
  Iterate should hunt cuts if any new rule turns out to be a no-op.
- **Owner reservations.** The owner explicitly did not endorse every conclusion of the source
  evaluations; the rejected-items section records this session's own filter, but the owner has
  not itemized which conclusions they doubted. If one of the *adopted* items was among them, the
  corresponding edit should be re-litigated.
- **Scale guidance is a comment, not a rule.** The Findings-map trigger ("past ~10 findings")
  lives in a skeleton comment; whether comments in the skeleton carry enough force is untested.

## Reviewer checklist

- **Session-vs-skill triage** — the report's central judgment. Check: for each *adopted* item,
  was the pre-edit rule genuinely silent (gap), or merely violated (compliance)? Overturned if a
  pre-edit rule already covered the behavior — that edit is then additive-default patching.
  Sharpest candidates: FF4 (was "few-line" already sufficient?) and the Status recast.
- **The FF1 rejection.** Check: is "fix the claim where it stands" truly operational, or does the
  prepend-next-to-stale-claim failure reveal an ambiguity in "lands at the claim"? Overturned if
  a reasonable reading permits the observed prepend — then FF1 was a skill problem and needs a
  recast, not a rejection.
- **The plan-item-7 no-op call.** Check: one compliant record ≠ evidence the behavior is default;
  the record was written by an unusually careful session. Overturned if a future thread hits
  Close with undiscovered reconciliation debt.
- **`Rejected write resets to purpose` placement.** Check: it fires mid-session, but the agent
  reads the skill at invocation — will it recall the rule at the moment of rejection?
  [speculation] A forcing function ("state the derivation before rewriting") was chosen to make
  compliance observable; overturned if oscillation recurs with the derivation stated pro forma.
- **Cold-safe falsifier** — the next session (or the owner) has to ask what a fresh entry means.
- **One-home falsifier** — the same number/definition appears verbatim in two sections.
- **Boundary falsifier** — one item sits on both the Planned list and the tracker.
- **Sync falsifier** — a count referencing an evidence base that grew this session survives stale
  in any section.
- **Paths falsifier** — an envelope closes with a non-resolving outgoing link.
- **Tag-default falsifier** — an untagged agent inference sits under an `[owner]`-class default.
