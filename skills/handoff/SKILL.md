---
description: "Brief a fresh session to continue an unfinished thread (context running out) or split off a side-thread. Writes HANDOFF_<topic>.md."
argument-hint: "[continue|split] <topic> — mode inferred if omitted, e.g. /handoff split tuning-metrics"
---

You're writing a **handoff**: a self-contained brief that lets a fresh session — zero memory of this chat — resume the work safely without redoing it. The receiver is a capable agent that will re-reason, not a step-follower. Two constraints: it reads **cold**, so name every file/section/decision it needs (nothing "as discussed"); and writing this **spends the context you're short on**, so it freezes what's settled and points at what's live — capture the decisions, their rationale, the current state, and the invariants the next session must preserve; point at the sources it should re-derive from. Anything bulky or still-moving stays a pointer, in its canonical home.

For careful edits to critical documents, use `/handoff-edit` instead.

## Setup
1. **Mode + focus** from the argument. First token `continue`/`split` is the mode (infer and state it in one line if omitted). The rest is a short free-text description of what the handoff covers — use it as the focus and scope, and derive a kebab-case slug from it. If the argument is omitted, infer the focus from the conversation (it should be obvious).
2. **Topic folder + AGENTS.md.** Save as `HANDOFF_<slug>.md` in the work's folder; point the receiver at its `AGENTS.md` — don't re-read the corpus yourself. **Write the handoff in the language the host's documents use** (check that `AGENTS.md`), not the chat's — English unless the corpus says otherwise. If a handoff for this topic already exists, **don't silently overwrite or spawn a near-duplicate** — update the existing file, or reconcile the slug with the owner. Duplicate handoffs fragment state.
3. **Never touch `scratch/`** as source or destination — except one file the owner explicitly names.

## Modes (same skeleton, different emphasis)
- **continue** — unfinished thread, fresh session. Emphasis: settled-vs-open, and the decisive next action.
- **split** — a side-thread that shouldn't pollute the current focus. Emphasis: the scope boundary, with an explicit "out of scope for the parent → here" pointer; carry only the minimum context.

## Skeleton (in order)
- **Title + focus.** `# Handoff — <focus> (<mode>)`, one-line single focus, `For:/From:/Date:/Status:`. Absolute date.
- **Read first (in order).** Each source with why + section; `AGENTS.md` first; code by path. Pointers only.
- **Anti-anchoring.** The handoff is input to verify, not authority: re-derive from the primary sources; confirm every claim.
- **State — settled vs open.** Settled = don't relitigate. Open = live questions; mark the decisive one. Spend your words here.
- **Substance.** Only what's not recoverable from the sources. Tight.
- **Ownership.** Editable vs read-only files. If the work touches another thread's doc, don't edit it — draft a standalone note for its owner inline.
- **Next actions + gates.** Numbered, the *suggested* path (the receiver adapts if its reading differs). Mark anything gated on data/decision/approval.
- **Data hygiene** (only if data's involved). Directed reduction: name the computation, owner runs it and pastes the small result; never raw arrays; subagent only for exhaustive scans.
- **Cautions / out-of-scope.** Each with a pointer to where it belongs; carry forward any `AGENTS.md` failure mode.
- **Closing note for the recipient.** End the handoff by telling the receiver two things: (1) when the work is done, propose capturing it as a `REPORT_<slug>.md` via `/report`; (2) its analysis and decisions **will be reviewed** — so keep the reasoning auditable as it goes (state the basis for each claim, flag inferences), not reconstructed afterward.

A handoff is forward-looking only — not a record of this session (that's a separate `REPORT_*.md`, on request). Don't fold a session log in.

## Before saving
Re-read cold: can every next-action be acted on without a question? Do all referenced paths exist (verify if unsure)? Settled separated from open, focus unambiguous, scope boundary explicit? Volatile values in their canonical home, dates absolute? Cut any transcript a pointer would replace.

## Saving
Write to `<topic-folder>/HANDOFF_<slug>.md`, never `scratch/`. Don't echo the doc back (you're offloading context) — confirm only: path, mode, one-line focus, scope boundary, and counts of reading items and next-actions. Offer to hand off a second thread if more than one surfaced.
