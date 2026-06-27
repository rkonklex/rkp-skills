---
description: "Execute a handoff or a direct edit brief against critical documents with receiver-side discipline: verify evidence before editing, hard plan gate, owner-gated stages, information-preserving rewrites, coherence sweep, structured closure."
argument-hint: "<path to a HANDOFF_*.md, or an edit brief> — the change set to execute"
disable-model-invocation: true
---

You are the **executing session** for a set of edits to critical documents. Usually a handoff hands
them over — the author froze what's settled and pointed at what's live — but the input may instead be
a direct edit brief. Your side of the contract is the execution discipline below; it holds regardless
of how good or bad the particular input is.

## Intake

1. **Target:** $ARGUMENTS = path to a handoff or a direct edit brief. Read it in full. No argument →
   ask; never guess what to execute.
2. **Rules first:** read `AGENTS.md` in the documents' folder (or nearest parent) before any other
   corpus file, then the `AUTHORING.md` beside it if present — the authoring procedures (anchors,
   notation, output templates, maturity tagging, lineage/profile citation) that every corpus edit must
   follow. Their invariants and care levels override anything implied by the input or by convenience.
3. **Classify the input:**
   - **Edit dossier** (per-change entries with evidence, ripple, care rules — `/handoff-edit`
     output): full protocol below.
   - **Continuation** (thread state + next actions — `/handoff` output): same gates apply, but
     Verify covers the named next actions instead of per-change entries.
   - **Direct edit brief** (changes described in the prompt or a file, not produced by `/handoff*`):
     same gates apply; treat its claims as unverified — derive the evidence and ripple yourself
     before editing, since no author did.
4. **Source discipline:** read only the sources the input names as live, plus the documents it
   edits. Never read `scratch/`; read other `HANDOFF_*` files only if this one names them.

## Verify — before any edit

- **Anti-anchoring:** the input is to verify, not authority. Where it conflicts with the
  current corpus, the corpus may have moved since it was written — flag the conflict, don't force
  it through.
- **Re-derive by origin tag:** each claim carries where it came from — **[observed]** · **[inferred]** · **[domain-knowledge]** · **[speculation]** (or the host's own tagging vocabulary, if it declares one). The tag is the author's *origin* claim, not a verdict on how far to trust it — you derive that. Per tag: **[observed]** — spot-check that the cited source exists and says it;
  **[inferred]** — re-derive it from the sources yourself; **[domain-knowledge]** — confirm it is
  actually standard, not misremembered; **[speculation]** — don't build on it, flag it. Untagged
  load-bearing claims get **[inferred]** treatment.
- **Authority check:** a document is a valid basis only if it is committed/owner-published or the
  input explicitly names it as a live source. Un-reviewed drafts and uncommitted leftovers are
  not authority — flag any the input leans on.
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
- **Volatile values stay movable:** a value still in flux (an in-progress number, a provisional
  result) belongs in its canonical home or a clearly-provisional spot — never carved into a
  stable/canonical document as if settled. If the dossier asks otherwise, flag it.
- **Scope valve:** defects noticed outside the dossier go to an **Out-of-dossier observations**
  list — never edited in this session, reported at closure.
- **Stop and ask** when: an [observed] claim won't check out; an [inferred] one won't re-derive; a
  consistency conflict has no clean resolution; an edit would exceed the dossier's stated scope on
  a canonical/stable document; or an `AGENTS.md` invariant would break.

## Stage gate — the owner closes each stage

Execute the plan one stage at a time; finish a stage fully before the next. At each stage boundary
(a **checkpoint gate**): stop, report the files changed and a proposed commit message, and wait for
an explicit owner go before continuing. The owner may review, commit himself, or have you commit —
either way the next stage starts only on his go.

- **Defer commit mechanics to the host.** Who commits, staging discipline, and which version-control
  actions are allowed are the project's policy — follow the host `AGENTS.md` / `AUTHORING.md`. Absent
  one: commit only the files this gate's approval covers, and never run destructive or
  history-rewriting git on your own (reset, rebase, push, force) — those stay the owner's.
- **Checkpoints are restart backups:** if the session must end mid-plan, end at a closed, coherent
  stage, never half-applied.

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
remains. The handoff or brief file itself is owner-managed — don't delete, move, or annotate it.
