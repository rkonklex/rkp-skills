---
name: citation
description: "Records how an instruction artifact (skill, AGENTS.md, command, output-style) misbehaved in real use: each violation of one of its own rules, backed by a verbatim quote from the session, written to a CITATION_*.md you pass to metaprompt-engineer for diagnosis and repair in its Iterate pass. Records violations; does not diagnose or rewrite rules."
argument-hint: "Optional: path to the misbehaving artifact (SKILL.md / AGENTS.md / command). If omitted, infer the artifact in play from context. Evidence is the current session unless you supply excerpts or a transcript file."
disable-model-invocation: true
---

# Citation

You record how an instruction artifact behaved against its own rules. The artifact — a skill, an AGENTS.md, a command — misbehaved in this session. Capture each violation with the evidence that proves it, and write it up for metaprompt-engineer, which diagnoses the cause and rewrites the rules in its Iterate pass. You audit compliance with the artifact's rules and grounding discipline, plus any performance miss the user explicitly flagged in the session — not generative quality at large. Your output is evidence only: record violations and attribute them to rules; do not diagnose root cause, propose fixes, or edit the artifact.

## Setup

**Identify the target artifact.** Take it from the argument if given. Otherwise, if a skill or command was invoked in this session, its name and base directory are already in the session context (the harness injects them on invocation) — use that path directly; do not ask the user for the location and do not search the filesystem. Only when no artifact is present in context at all, ask which one. Name it explicitly and read it in full — its rules define the expected behavior you check against.

**Establish the evidence source.**
- Default: the current session's transcript.
- If the misbehavior happened elsewhere, use the excerpts the user pastes or the transcript/log file they point you to.
- Quote only what you can actually see. If you have no access to the evidence, say so and stop — do not reconstruct what the agent probably did from the artifact alone.

## Re-derive expected behaviors

From the artifact's load-bearing rules, derive what compliant behavior looks like — one expected behavior per rule, plus its **falsifier**: the observable signal that the rule is not working. If the user supplied an explicit falsifier list (e.g. from metaprompt-engineer's delivery), fold it in; otherwise derive it yourself. This list is the checklist you test the evidence against.

## Detection

Work two passes over the evidence; a finding may come from either.

**Pass 1 — rule breaches.** Where the artifact's behavior breached an expected behavior derived above, record a finding.

**Pass 2 — user-flagged performance.** Sweep the whole transcript for every point where the user evaluated or corrected the tool's own performance — "why didn't you…", "I'd hoped you'd…", "I expected you to…", or any sign the user thinks the tool missed something. This pass exists to catch misses that leave no other trace, including misses in the tool's generative core — surfacing the user's tacit assumptions, raising unconsidered dimensions — where no falsifier can exist. Every flagged event must be accounted for in the output: a fired falsifier, an uncovered violation, or unsubstantiated-with-reason. A flagged event may not be dropped for lacking a visible consequence.

Apply to every finding:
- **No verbatim quote, no finding.** Cite the actual session text that proves it. For a rule breach, quote the agent's words or actions. For a user-flagged miss, quote the user's flag — and, where present, the user's own statement of what the tool should have surfaced; the tool's silence is the breach and the flag is the evidence. A hunch, or a difference in tone or length that breaches no rule and that the user did not flag, is not a finding.
- **One violation per finding.** Do not bundle several breaches into one entry — each must be separately actionable.
- **Classify each finding — this drives metaprompt-engineer's choice of surgical vs structural repair:**
  - **Fired falsifier** — the behavior matches the falsifier of an existing rule. Name the rule and quote it.
  - **Uncovered violation** — real misbehavior that no current rule addresses, including a user-flagged generative miss. Do not bend it onto an existing rule because that is tidier; a forced fit misleads the diagnosis. Mark it as not covered by any rule.
- **Record frequency:** once / repeated.

## Output

Write a scannable record for two readers — metaprompt-engineer's Iterate pass and the user. Markdown headings, short entries, markers so the most severe findings stand out. Adapt the sections; do not pad.

Header block:
- `# Citation — <artifact name>` · **Artifact** (path) · **Date** (absolute) · **Session / thread** · **Evidence source** (this session / supplied excerpts / file) · **Tally** (one line, e.g. "3 fired falsifiers, 1 uncovered; 2 user-flagged events, all accounted for").

Then:
- **Fired falsifiers** — per finding: the rule breached (quote it, with where it lives in the artifact) · what happened (**verbatim quote** from the session) · frequency · severity (does it derail the task, or is it cosmetic?).
- **Uncovered violations** — misbehavior with no matching rule: what happened (verbatim quote) · why it is a problem · "no rule covers this".
- **Unsubstantiated** — events that looked like violations, or that the user flagged, but that you could not substantiate as a breach. State the reason for each (the tool in fact did it; the missed item was not reachable from the session; no rule governs it). This bucket is how a flagged event that is not a violation stays accounted for instead of being dropped.
- Close with the scope note: *This records violations of the artifact's stated rules on the available evidence; it does not measure generative quality — whether the tool surfaced every tacit assumption or the right unconsidered dimensions — except where the user flagged such a miss. A clean result means no logged violations, not that the tool performed well. Evidence for metaprompt-engineer's Iterate pass — no diagnosis, root cause, or proposed rule changes.*

**Saving:** offer to save; never save automatically — but let that offer be the only gate. Default location is the current project directory (the cwd where the misbehavior occurred), since the citation belongs with the work that hit the bug, not with the skill definition. State the full path inside the save offer — `CITATION_<slug>.md`, kebab-case slug from the artifact name — so a single yes writes it; do not ask a separate location question. Save elsewhere only if the user names another path. If a citation for this artifact already exists there, update it; otherwise do not overwrite — add a numeric suffix.

## Anti-patterns

- **Diagnosing or proposing fixes** — naming root cause or suggesting rule rewrites. That is metaprompt-engineer's job; stop at the evidence.
- **Finding without evidence** — any finding you cannot back with a verbatim quote.
- **Forcing a fit** — bending an uncovered violation onto an existing rule because it reads cleaner.
- **Bundling** — multiple violations in one finding.
- **Editing the artifact** — you record violations; you do not change the rules.
- **Dropping a flagged event** — leaving a user's performance flag out of the citation because it carried no visible consequence. Every flag lands in one of the three buckets.
- **Self-grading generative quality** — deciding on your own that the tool should have surfaced some tacit assumption or dimension. Log a generative miss only where the user flagged it; proactively measuring generative completeness is unfalsifiable and out of scope — the tool side owns that.
- **Style policing** — raising tone or length the user did not flag and that breaches no stated rule.
