# CLAUDE.md — rkp-skills

This repo is a Claude Code skills plugin (`rkp`). Each skill is one
`skills/<name>/SKILL.md`; the folder name is the skill id, invoked `/rkp:<name>`.
Working here means **authoring and refining instruction artifacts**, not running them.

## Two layers — keep them straight
- **This file** governs editing *this* repo: it is the authoring contract for the skills.
- **A skill at runtime** operates on the *host project's* corpus — a different corpus the user
  points the skill at, governed by that project's own rules (see House voice). Don't apply this
  file to a skill's runtime behavior, or a host's rules to repo edits.

## Registry sync — forcing function
A skill is recorded in four places. Any add / rename / remove updates all that apply, in the
same change:
- `skills/<name>/SKILL.md` — the skill.
- `README.md` — the catalog row **and** the matching "How they fit together" line.
- `.claude-plugin/plugin.json` — the `description` if the set's character changed.
- `.claude-plugin/marketplace.json` — the plugin `description` there, same trigger.

A rename also sweeps cross-references: skills cite each other bare (`/handoff`, `/report`).
Grep both the old and new name across `skills/` and `README.md` before closing the change.

## SKILL.md frontmatter contract
- **Write `description` as a trigger, not a blurb:** for an auto-discoverable skill it is the
  only signal the model fires on. State *when to reach for it* in the user's terms — not what
  the skill is proud of.
- **Set `disable-model-invocation: true` for deliberate tools** — ones the user must choose
  (audits, rebuilds, adversarial dialogue). Omit it only when auto-firing on a description
  match is genuinely wanted.
- **`name` is optional; the folder name is the source of truth.** If `name` is present it must
  equal the folder name.
- **`argument-hint` states the args plus one worked example.**

## House voice — match it or the set frays
Every `SKILL.md` here shares one discipline; a new or edited skill conforms to it:
- **Tag-driven imperatives:** each rule is a bold semantic tag + an imperative verb, not prose.
- **Claims carry their origin — sender states, receiver re-verifies:** tag anything past the
  evidence with one closed origin set — `[observed]` (read directly from data, a measurement, or
  a quotable source) · `[inferred]` (derived, not directly seen) · `[domain-knowledge]` (general
  expertise, uncited) · `[speculation]` (a guess). The tag is a *fact about where the claim came
  from*, never the sender's self-rating of how far to trust it — the receiver derives that from
  the origin. Tag by how you came to hold *this* claim, not its inputs: a derived claim stays
  `[inferred]` even when its inputs were measured. The four-tag set is the authoring default,
  not a fixture: a skill presents it as replaceable by the host's declared provenance
  vocabulary, with the mapping recorded at promotion. **Maturity/confidence** (`✓/~/⚠`,
  likely-holds/…) is a separate axis; **movability** (provisional, will-move) is structural —
  where a value lives, not a tag.
- **Flag, don't decide:** surface findings for the owner to adjudicate; never silently pick a
  winner or edit canonical material without an explicit gate.
- **Anti-sycophancy:** push back as a peer; steelman, then object, before any endorsement.
- **Cold-safe artifacts:** whatever a skill writes (`HANDOFF_` / `REPORT_` / `NOTE_` /
  `CITATION_`) must read without the originating chat.
- **Mark load-bearing rules, and give each a falsifier:** name the few rules that void the tool
  if broken, and the observable signal that proves one failed.
- **Conform to the host, don't reload it:** the harness loads the host project's rules into context,
  so a skill **assumes they're there and conforms** — its own defaults lose to them on conflict —
  and never re-reads or enumerates rulebook filenames. It reads only what the harness won't load: a
  doc the rules **name** (e.g. `AUTHORING.md`), or a plain orientation doc for structure. Preparing
  the project for its harness is the *project's* job, not the skill's. Match the host's document
  language, not the chat's.

## No build step
Nothing here compiles, lints, or tests. Validation is reading: the frontmatter parses, the four
registry places agree, cross-references resolve. Don't invent a CI process or a validator command.
