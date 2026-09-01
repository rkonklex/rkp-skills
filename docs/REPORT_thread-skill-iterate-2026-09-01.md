# REPORT — thread skill Iterate pass, 2026-09-01

Iterate pass over `skills/thread/` (SKILL.md + LINT.md), plus one rule in the user-level
instruction file. Evidence: two field citations from one host session (35 logged items:
29 fired falsifiers, 6 uncovered violations, across two phases). Per the repo contract,
host material stays with the host — items are described by class only.

## Triage

35 items → 7 actions. 22 closed with no change (live rules that fired and were caught by
the panel, the arbiter, or the owner — rewording rules that already say the right thing
was rejected; this skill's history shows reworded rules re-failing within days). 2 dropped
on the owner's instruction. Deferred to the next pass: a scope/over-generalization lint
charge and an ambiguity charge, pending field data on what the arbiter changes.

## Additions gated per PROVE.md (fresh-context agents; adversary on the frontier tier,
arms on the mid tier, lint benchmark on the field tier)

**Gloss rule (chat first-mention expansion, thread SKILL.md).** Adversary: NOT-REDUNDANT;
its smallest variant widened the existing ids-with-titles clause instead of adding a rule.
Arms on the adversary's scenario (status summary from a record with anchored shorthand;
binary observable: every record term explained at first occurrence without cross-jargon):
none 3/3 fail · variant 3/3 pass · off-target 3/3 clean. **Variant shipped.**

**Shell-splice ban (user file).** Adversary: NOT-REDUNDANT (harness guidance is soft and
mode-dependent); found the proposal's hole — "file tools" blesses whole-file Write rewrites
from stale reads — and closed it in the variant. Arms (bulk rebrand over a doc with two
must-survive old-name sites; observable: byte-exact survival of a CDN URL): none 0/3 fail ·
variant 0/3 · off-target (whole-word code rename) 3/3 clean, blind-substring trap avoided.
**Null on necessity — ships unproven.** The field failure's mechanism (auto-mode shell
steering, hour-old reads, parallel sessions) is the session-pressure case PROVE.md's limit
note names; corroboration recorded there.

**Reconstructable-method clause (Cold-safe entries).** Adversary: NOT-REDUNDANT
("reads without the session" is a comprehension bar, not a reconstruction bar). Arms
(write a probe entry from a to-be-discarded script with four non-obvious details): none arm
produced complete specs — the fixture over-cues, the script's comments narrate the traps;
variant runs produced exemplary specs plus NaN/ordering detail; off-target (booking a
non-computed tracker item) 3/3 clean, no spec demands. **Null on necessity — ships
unproven**; same instrument-limit class.

## Lint protocol change, benchmarked

LINT.md restructured: panel runs once per checkpoint (never re-runs on its own fixes),
then a two-agent arbiter loop with a consequence-based severity bar, a verdict token
(`ACCEPT` / `FIX (n)` / `REWORK`), cosmetic flags reported and never fixed, three-round
cap then escalate. Narration/cold charge gains flag attribution (`[this session]` /
`[pre-existing]`). Economy charge untouched — its benchmark carries.

Controlled pass on a synthetic record + generated diff (planted: 4 this-session
narration/cold violations, 1 pre-existing violation in a touched section, 2 content
errors — a cross-site numeric disagreement and a false citation — plus cosmetic bait):

- Narration/cold + attribution, 2 agents: 4/4 plants each; pre-existing correctly
  quarantined by both; one agent also surfaced both content errors.
- Arbiter, 2 agents: verdicts FIX(2) and FIX(5); the BLOCKING union contains both planted
  content errors while each single arbiter missed one — the union rule is load-bearing,
  reproducing the field's disagreement pattern. No cosmetic promoted to blocking; no
  cosmetic fixed.

## Field record behind the arbiter (from the host session, by class)

Exercised ad-hoc mid-session: two rounds with fixes between, terminated ACCEPT/ACCEPT on
the third; surfaced two content errors four rounds of the flag-list panel had missed; the
two arbiters disagreed on both rounds, which the union rule absorbs. Not yet exercised on
a high-defect write (field rounds each returned one blocking issue).
