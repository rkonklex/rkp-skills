---
description: "Epistemic audit of a research corpus: reconstruct the implicit model of the subject, surface gaps, expose load-bearing assumptions, and challenge the framing from first principles. Not a consistency check — this interrogates whether the model is complete and correct as a description of the real subject."
argument-hint: "Optional. A directory, or space-separated document paths / bare filenames resolved against the target directory. If omitted, audits the living documents in the current topic directory. Example: signal_model.md operations.md"
disable-model-invocation: true
---

You are conducting an epistemic audit of a research corpus. This is not a consistency review. Reconstruct the model of the subject that is embedded in these documents, then examine that model critically — finding what is missing, what is assumed without justification, and where the framing may be wrong or suboptimal.

All documents are working hypotheses about the subject, not authoritative specifications. Some are more stable than others, but none are oracles. Your authority is the first principles of the subject domain and established domain knowledge — not the documents. The documents are inputs to interrogate, not ground to stand on.

## Setup — orient to the corpus

**Resolve the document list:**

- If arguments name a directory → audit the living documents in it.
- If arguments name files → for each argument with no path separator, resolve it against the target directory; use the resulting paths.
- If no arguments → audit the living documents in the current topic directory.
- If the corpus has a document map / index (e.g. `index.md`), read it first to resolve the corpus.

**Identify the canonical reference:** Read `AGENTS.md` and `README.md` in the target directory — and the root project directory if neither is there. They typically name the key documents and the most stable / canonical reference. State your inference explicitly, then read that document before the others. Treat it as the best available starting point, not as settled fact — its assumptions and conclusions are in scope for challenge. If no canonical reference can be identified, proceed without one and note the absence.

**Harvest the corpus's conventions (limited degradation).** From the rulebook (`AGENTS.md`, plus any authoring / conventions / style document it names), extract what the audit needs:
- **Maturity vocabulary** — the tags the corpus uses to mark confidence or validation (e.g. Established / Provisional / Exploratory) and which claims it treats as settled.
- **Anchor / citation convention** — how stable references are written (e.g. `{#id}` anchors); used in Step 1 citations.
- **Frozen layer** — which files are historical records or superseded (e.g. `REPORT_*`), to be challenged only as link-targets, never reconstructed as the live model.
- **Document language** — the language corpus files are written in.
- **Domain constraints & known failure modes** — hard limits of the subject the corpus declares (geometry, topology, dimensionality, prior trust-breaks).

Try the obvious sources for each. If the corpus declares no usable structure for a given convention, **say so explicitly and fall back to the generic default**: rate maturity on a plain confidence axis; cite file + section heading; treat nothing as frozen unless it self-identifies as a historical record; write in the chat's document language; impose no domain constraints beyond standard domain knowledge. Do not invent conventions the corpus does not have.

**Exclude from the audited corpus:** this skill's own outputs (`epistemic-audit-*.md`), instruction / convention files (`AGENTS.md`, `README.md`, authoring docs — they are convention sources, not model content), handoff files (in scope only when passed explicitly as arguments), the harvested frozen / historical layer, and directories starting with `.` or named `scratch`.

## Step 1 — Model Reconstruction

Extract and write out the implicit model of the subject as you understand it from the documents. This is a synthesis task, not a summary.

**Choose the decomposition the subject demands.** Start from this domain-neutral scaffold and rename or replace facets to fit the actual subject:
- **Entities** — the objects or quantities the system is built from.
- **Mechanisms** — how they generate behavior, interact, and vary.
- **Constraints** — the physical, topological, operating, or architectural limits.
- **Observables** — what is measurable or inspectable, and through what chain.
- **Outputs** — the scalar metrics or decisions that characterize the system, and what they support.

The scaffold is a starting point, not the spec — adapt it. *Worked examples (do not copy verbatim):* a physical-measurement corpus decomposes naturally into signal / noise / hardware / measurement / metric; an algorithm rewrite into inputs / state / transformations / invariants / outputs; an agent or operating-contract corpus into actors / rules / triggers / escalation / outcomes. Use whichever decomposition exposes *this* subject. If the host `AGENTS.md` declares its own model facets, prefer them.

Be concrete, but do not transcribe. State each claim in one line and cite it using the corpus's anchor convention (or file + section heading if it has none). Reproduce full equations, formulas, or specifications only where there is tension, ambiguity, or a silence to expose. A paragraph that restates what a document already says cleanly is a violation — cite it instead. Where the documents are silent on something that clearly matters, note the silence in-line — those silences are the raw material for Step 2.

This step produces the foundation for the rest of the audit.

## Step 2 — Gap Analysis

What should be in the model that is not?

For each gap, state:
- What is missing and why it matters for the use cases or decisions the work supports.
- Whether this is a **documentation gap** (the knowledge exists, it was not written down) or a **knowledge gap** (the question is unresolved).

Only flag gaps that would materially affect a metric, procedure, or conclusion. Do not pad.

## Step 3 — Assumption Audit

What does the model assume — explicitly or implicitly — that may not hold?

Focus on load-bearing assumptions: ones where, if wrong, a metric, procedure, or conclusion is invalidated.

For each assumption:
- State it precisely.
- Identify where it appears: explicitly stated vs. implicit in a formula or procedure.
- Challenge it: under what conditions does it break, and what is the effect?
- Rate it: **likely holds** / **uncertain** / **likely wrong**.

Prioritize by maturity using the harvested vocabulary: concentrate on the most mature, most relied-on claims. Rating an already-low-maturity item (provisional, exploratory, candidate) as merely *uncertain* adds nothing — challenge it only when you can be sharper than its tag already is (e.g. *likely wrong*, with the breaking condition). If the corpus has no maturity vocabulary, prioritize the claims the conclusions and decisions most depend on.

## Step 4 — Frame Challenge

Set the existing document structure aside. Reason from the subject outward.

- Is this the right set of metrics / outputs for the use cases? Is anything important unmeasurable with the current set, or is something being measured that does not discriminate between relevant states of the system?
- Is the chosen decomposition the most natural one for this subject? Would a different decomposition expose something the current framing hides?
- Are the use cases or scenarios addressed the right ones? Are there important operating scenarios or failure modes not represented anywhere?

This step is generative, not critical. Surface sharp questions, not vague dissatisfaction. If you have no genuine challenge, say so explicitly — do not manufacture criticism.

## Output Format

Present the four steps in order as direct markdown — headings, bullet points, and equations rendered normally. Do not wrap any part of the output in a code fence. Use section headers matching the step names.

Write the audit in the corpus's document language (harvested above), not the chat's — it may be saved verbatim as a corpus file.

There are no severity ratings here. The output is a structured analysis, not a findings list.

When speculating beyond what the documents explicitly support, label it clearly: *[inference]* or *[domain knowledge, not in documents]*.

After presenting the full audit, offer to save it to a file. Do not save automatically.

## Saving the audit

When the user asks to save — immediately after the audit or after a discussion that refined it — write the full audit as it stands at that point to `<target-directory>/epistemic-audit-<YYYY-MM-DD>.md` using today's date (target directory = the audited directory, or the parent of the audited files). If that filename already exists, append a sequence suffix (`-2`, `-3`, …) instead of overwriting. Checking for filename collisions is allowed; reading the content of any existing audit file is not.

## Constraints

- **Hold authority in the subject, not the documents.** When the canonical document contradicts domain knowledge or first principles, name the contradiction — never treat a claim as settled because it appears in the most stable document.
- **Classify each finding as gap or error.** A gap is a missing piece of the model; an error is a mistake in the documents. Do not conflate them.
- **Ground every domain claim.** Support it from the documents or from standard domain knowledge; if neither supports it, say so explicitly rather than asserting it.
- **Respect the harvested domain constraints.** Honor the hard limits and known failure modes the corpus declares (e.g. dimensionality, topology, prior trust-breaks); reason inside them, and flag — never silently cross — any proposal that would violate them.
- **Stay diagnostic.** Surface gaps, assumptions, and frame challenges; do not propose redesigns or rewrites — that is a different skill.
- **Skip this skill's own outputs.** Never read any file matching `epistemic-audit-*.md` — they are artifacts of previous runs, not corpus content.
