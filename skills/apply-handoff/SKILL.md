---
description: "Execute a HANDOFF_*.md against critical documents with receiver-side discipline: verify evidence before editing, hard plan gate, guarded checkpoint commits, information-preserving rewrites, coherence sweep, structured closure."
argument-hint: "<path to HANDOFF_*.md> — the handoff to execute"
disable-model-invocation: true
---

You are the **receiving session** of a handoff. The author froze what's settled and pointed at
what's live; your side of the contract is the execution discipline below — it holds regardless of
how good or bad the particular handoff is.

## Intake

1. **Target:** $ARGUMENTS = path to the handoff. Read it in full. No argument → ask; never guess
   which handoff is meant.
2. **Rules first:** read `AGENTS.md` in the handoff's folder (or nearest parent) before any other
   corpus file, then the `AUTHORING.md` beside it if present — the authoring procedures (anchors,
   notation, output templates, maturity tagging, lineage/profile citation) that every corpus edit must
   follow. Their invariants and care levels override anything implied by the handoff or by convenience.
3. **Classify the handoff:**
   - **Edit dossier** (per-change entries with evidence, ripple, care rules — `/handoff-edit`
     output): full protocol below.
   - **Continuation** (thread state + next actions — `/handoff` output): same gates apply, but
     Verify covers the named next actions instead of per-change entries.
4. **Source discipline:** read only the sources the handoff names as live, plus the documents it
   edits. Never read `scratch/`; read other `HANDOFF_*` files only if this one names them.

## Verify — before any edit

- **Anti-anchoring:** the handoff is input to verify, not authority. Where it conflicts with the
  current corpus, the corpus may have moved since it was written — flag the conflict, don't force
  the handoff through.
- **Re-derive by evidence tag:** tags follow the host corpus's basis scheme if it declares one — the axis for what a claim *rests on* (origin/provenance), not its validation status or file placement — else the dossier defaults **[V]** verified by data · **[I]** inferred · **[P]** provisional. Per tag: **[V]** — spot-check that the cited source exists and says it;
  **[I]** — re-derive the inference from the sources yourself; **[P]** — treat as movable, never
  write into a stable document. Untagged load-bearing claims get [I] treatment.
- **Authority check:** a document is a valid basis only if it is committed/owner-published or the
  handoff explicitly names it as a live source. Un-reviewed drafts and uncommitted leftovers are
  not authority — flag any the handoff leans on.
- **Plan:** produce the execution plan — ordered stages; per stage the files touched; which edits
  are owner-gated (canonical documents, items marked as needing approval); the dossier's open
  calls with your proposed resolutions; anything that failed verification.

## Plan gate — hard

Present the plan and **stop**. No file is touched before approval. Approval covers the plan
shape, not the gated items: each owner-gated edit re-asks at its point of execution with the
drafted wording in hand. Open calls are resolved at this gate or explicitly deferred to their
stage.

## Execute

- **Stage order:** follow the approved plan; finish a stage fully before starting the next.
- **Inventory before rewrite:** before replacing or restructuring any existing section, table,
  card, or figure, enumerate its information elements (fields, values, units, caveats, anchors,
  diagrams). After the rewrite, account for each element: *kept / moved to X / dropped — reason*.
  Show the dropped list at that stage's checkpoint gate. This applies to every rewrite that
  replaces existing structure, not only tables.
- **Voice match:** write new prose in the surrounding document's voice, density, and notation
  (markup, math style, symbol formatting of adjacent lines). Repeat a full disambiguating name only
  where the distinction is load-bearing; elsewhere let context carry it.
- **Present-state prose:** living documents state what is, never what changed or why it changed
  just now. No "for now", "the older workflow", "this compromise" — moment-in-time rationale
  belongs in the report or roadmap, not in a spec or playbook.
- **No phantom referents:** never reference a policy, section, threshold, or procedure that does
  not exist in the corpus. If a sentence needs a referent, point at the concrete artifact that
  exists, or flag the gap to the owner — don't invent the artifact to make the sentence work.
- **One home for a repeated rule:** when an edit replaces a rule that is restated in several
  places, write the full statement once in its canonical home; every other site gets a
  self-contained one-liner (actionable without a lookup — no bare "see §X" bounces) and at most
  one concept-level link. Verify the canonical statement covers every trigger its dependents cite.
- **Conservative defaults:** where the dossier leaves a judgment call open (a rating, the strength
  of a claim, scope of a statement), pick the conservative option and flag any promotion to the
  owner.
- **Scope valve:** defects noticed outside the dossier go to an **Out-of-dossier observations**
  list — never edited in this session, reported at closure.
- **Stop and ask** when: a [V] claim won't reproduce; an [I] inference won't re-derive; a
  consistency conflict has no clean resolution; an edit would exceed the dossier's stated scope on
  a canonical/stable document; or an `AGENTS.md` invariant would break.

## Git protocol — the index is the owner's

The working tree is yours to edit; **the index and history are the owner's review surface** (the
owner stages work to inspect diffs). State-changing git commands happen only at checkpoint gates,
never spontaneously — a git mutation outside a gate is a protocol breach.

- **Commit mode is set at the plan gate:** agent checkpoint commits (the protocol below), owner
  commits, or working-tree only (no git mutations at all — e.g. cleanup layered on an existing
  staged change). Ask; don't assume. In working-tree-only mode, stage boundaries still gate via
  the changed-files report.
- **Checkpoint gate** at each stage boundary: report the files changed and a proposed commit
  message; wait for an explicit go. The owner may instead commit himself — then wait for his
  confirmation before the next stage.
- **On go, guarded commands only:**
  1. `git status --porcelain` — if anything is staged that this gate's approval doesn't cover,
     stop and ask; never assume staged content is disposable.
  2. New files only: `git add -- <named file>` (each file named explicitly).
  3. Commit by pathspec: `git commit -m "<msg>" -- <named files>` — this commits only the named
     files and leaves the rest of the index untouched.
  - Never a bare `git commit`; never `git add -A` / `-u` / `.`; nothing beyond add/commit — no
    reset, restore, stash, rebase, or push. Those are the owner's.
- **Checkpoints are restart backups:** if the session must end mid-plan, end it at a committed
  coherent stage, never half-applied.

## Context watch

If context pressure threatens quality mid-plan: finish and checkpoint the current stage, then
write a continuation handoff (`/handoff`) for the remainder instead of degrading through the tail
stages.

## Cohere — after the last stage

One light pass over the touched documents read together (not per-edit):

- **Retired-term sweep:** grep for every name, label, or framing retired — build the list from
  the dossier *and* from the edits actually made (every rename counts, whether the dossier named
  it or not), plus stock transient phrasing (`for now`, `currently`, `compromise`, `under
  investigation`); expect zero hits outside frozen reports.
- **Consumer sweep:** for each changed definition or domain, grep the changed symbols themselves
  across the whole corpus — including files the dossier never named — and read every hit
  (examples, intros, notes, limitations) checking that the *claim* still holds, not merely that no
  retired token appears. Secondary prose paraphrasing the old semantics is the main leak.
- **Anchor check:** every `{#id}` and cross-reference added or repointed resolves.
- **Invariant spot-check:** the `AGENTS.md`/index rules relevant to the touched documents (link
  direction, no code in docs, where volatile values live) still hold.
- **Render if available:** run the corpus build (e.g. a docs/site build like `quarto render`) when the tool is present;
  if unavailable, report that plainly — never imply render validation that didn't run.

Fixes from this pass go through a final checkpoint gate.

## Close

Report, in this order:

1. Per dossier change: **applied / adapted (how) / skipped (why)**.
2. Open calls and how each was resolved or deferred.
3. Out-of-dossier observations.
4. Verification run vs not run — stated plainly.

Then **propose, don't write**: `/report` for a durable record; a continuation handoff if residue
remains. The handoff file itself is owner-managed — don't delete, move, or annotate it.
