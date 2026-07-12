---
name: handoff-edit
description: "Hand off careful edits to critical documents as an evidence-backed change dossier for a fresh session to execute. Writes HANDOFF_<topic>.md."
argument-hint: "<topic> — names the document-edit thread, e.g. /handoff-edit auth-retry-policy"
---

You're writing a **handoff-edit**: a brief that hands the careful editing of critical documents to a fresh session. Research and decisions are done; the edits aren't made here because this context is heavy and an overflow mid-edit could compact and corrupt the documents. A capable model makes them in a clean session with room to deliberate — reading the docs fresh, verifying the case, writing the prose itself, watching the whole corpus for consistency.

So this is a **change dossier, not a diff** — a keystroke script would waste the receiver's judgment. Equip its thinking; don't replace it. It reads cold (name every file/section/decision), so it **freezes what's settled and points at what's live** — capture the evidence, the rationale, and any invariant the edits must preserve; point at the sources the receiver should re-read and re-derive from.

For continuing or splitting a thread, use `/handoff`.

## Setup
1. **Focus** from the argument — a short description of what to edit; use it as focus and scope, and derive a kebab-case slug for the filename `HANDOFF_<slug>.md` in the documents' folder. If omitted, infer the focus from context. If a handoff for this topic already exists, **don't silently overwrite or spawn a near-duplicate** — update the existing file, or reconcile the slug with the owner.
2. **Authoring doc.** The receiver's harness loads the corpus's rules — don't re-read the corpus. But point the receiver at any `AUTHORING.md` the rules name: it carries the authoring procedures the edits must follow and is *not* auto-loaded.
3. **Never touch `scratch/`** as source or destination — except one file the owner explicitly names.

## The handoff (in order)
- **Title + focus.** `# Handoff (edit) — <focus>`, which docs change and to what end, `For:/From:/Date:/Status:`. Absolute date.
- **Read first (in order).** Sources with why + section; the docs to edit and any code by path. Pointers only.
- **Anti-anchoring.** The handoff is input to verify, not authority: re-derive from the sources before editing a critical doc.
- **State — settled vs open.** Settled = don't relitigate. Open = judgment calls left to the fresh session.

### Change dossier — per intended change
- **What & where.** Target doc + section, what it says now, what's wrong/missing. Name it precisely; **don't pre-write the replacement** — give intent, not keystrokes.
- **Why.** The driving conclusion; alternatives weighed and rejected; cost of leaving it.
- **Evidence, tagged by origin.** What justifies the change, or where it lives — and where each claim came from, so the receiver knows how far to re-derive: **[observed]** (take as-is; the receiver spot-checks the source) · **[inferred]** (re-derive from the sources) · **[domain-knowledge]** (confirm it's standard, not misremembered) · **[speculation]** (don't build on it, flag). The tag states origin, not how far to trust it — that's the receiver's call. If the host corpus declares its own tagging vocabulary (in the host's rules or a doc they name, e.g. `AUTHORING.md`), stamp in that instead. Movability — a provisional value that will move — is **not** a tag: route it through the Care rules below (volatile values to one canonical home), never carved into a stable doc.
- **Suggested direction.** Proposed wording, marked as an improvable starting point, not a mandate.
- **Consistency & ripple.** Where this reaches — invariants, sibling docs, terminology, dependent claims. Say where to look.
- **Open calls.** Where you were unsure; ask the receiver to deliberate, and what tips it.

### Care rules
- **Care level per target.** Which docs are canonical/stable (change only with owner approval) vs provisional. Volatile values (in-progress numbers, provisional results) live in one canonical home; others point there and state the class, not the figure.
- **Stop and ask** instead of pushing through when: an [observed] claim won't check out or an [inferred] one won't re-derive; an edit would touch a canonical doc; or a consistency conflict has no clean resolution.
- **Close with a whole-corpus coherence pass** — after all edits, one read-through of the touched docs and neighbours together (not per-edit), catching any invariant or cross-reference a change broke.

## Before saving
Re-read cold: can the receiver *verify the case* for each change without this chat? Do all paths exist? Settled vs open separated, in-play docs vs untouchable clear? Each change has tagged evidence + rationale, improvable wording, named ripple? Volatile values in their canonical home, dates absolute? Stop-and-ask triggers and the coherence pass present? Cut transcripts a pointer would replace.

## Saving
Write to `<topic-folder>/HANDOFF_<slug>.md`, never `scratch/`. Don't echo the doc back — confirm only: path, focus, docs in play, count of changes, and any canonical-doc edit needing owner approval.
