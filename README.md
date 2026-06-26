# rkp-skills

Robert Konklewski's Claude Code skills, packaged as a plugin (`rkp`).

These are **thinking and writing disciplines for research-style work** — developing an idea,
auditing a corpus of documents, handing work to a fresh session, recording what was decided, and
engineering the instructions that drive agents. They lean on a shared house style: cold-readable
artifacts, claims tagged by how solid they are, anti-sycophancy, and "flag for the owner, don't
silently decide." Most are corpus-aware — they read a folder's `AGENTS.md` / `AUTHORING.md` and
conform to the host project's conventions rather than imposing their own.

## Install

**Own machine (auto-load, no command):** clone this repo to `~/.claude/skills/rkp/`.
The `.claude-plugin/plugin.json` makes it load as `rkp@skills-dir` on the next session —
skills become `/rkp:<name>`. No marketplace, no `/plugin install`.

**Share with others / other distribution:** the bundled `marketplace.json` also lets anyone
add this repo as a marketplace and install it:

```
/plugin marketplace add <repo-url-or-local-path>
/plugin install rkp@rkp-skills
```

## Invoking a skill

Type `/rkp:<name>` (e.g. `/rkp:attack-duck`, `/rkp:handoff split tuning-metrics`). Each skill's
`argument-hint` shows what to pass.

Skills marked **slash-only** below have `disable-model-invocation: true` — Claude won't trigger
them on its own; you invoke them deliberately. The rest are **auto-discoverable**: Claude may reach
for them when the situation matches their description, and you can still invoke them by hand.

## The skills

### Think an idea through

| Skill | What it does |
|---|---|
| **attack-duck** *(slash-only)* | An adversarial thinking partner for a half-formed idea, observation, or decision. Develops it through dialogue — mirrors the idea back, surfaces hidden assumptions and blind spots, pushes back instead of agreeing, and (on your go) crystallizes the result into a `NOTE_<topic>.md` written for *you*. Works open, or grounded against a corpus. **Use to** pressure-test or structure an idea, decide whether it's worth doing, or make sense of observations against code/docs. |

### Hand work off, and record it

A small pipeline for moving work between sessions without losing or corrupting it.

| Skill | What it does |
|---|---|
| **handoff** | Briefs a *fresh* session to **continue** an unfinished thread (context running out) or **split** off a side-thread. Writes a cold-readable, forward-looking `HANDOFF_<topic>.md`: what's settled vs open, what to read, the decisive next action. **Use when** you're about to run out of context, or want to spin a tangent into its own thread. |
| **report** | Writes a durable, backward-looking `REPORT_<topic>.md` that **stands alone** — a reader with neither the chat nor the source handoff can follow the work and audit it. Dual-purpose: a human reference *and* auditable input for an AI review, with every claim tagged by basis. **Use when** capturing a finished session for the record or for review. |
| **data-investigation** | A partner for **investigating data that's partial, sensitive, or non-authoritative** — it designs the probe, you run it and paste back only the reduced result. It picks the smallest probe that discriminates between the live explanations and pushes back when a conclusion outruns the evidence. **Use when** chasing a metric, anomaly, or regression you can only see in part. |

### Edit critical documents safely

A two-sided protocol for changes that matter enough that a mid-edit context overflow could corrupt
the docs: one session writes the dossier, a clean session executes it.

| Skill | What it does |
|---|---|
| **handoff-edit** | The **author side**. Hands the careful editing of critical documents to a fresh session as an evidence-backed *change dossier* (intent + rationale + tagged evidence + ripple, **not a diff**) in `HANDOFF_<topic>.md`, so the editing happens in a clean session with room to deliberate. **Use when** the edits matter and you don't want to make them under a heavy context. |
| **apply-edit** *(slash-only)* | The **receiver side**. Executes a handoff or a direct edit brief against critical documents with verify-before-edit discipline, a hard plan gate, owner-gated stages, information-preserving rewrites, and a coherence sweep. **Use to** carry out a `HANDOFF_*.md` (or any edit brief) safely. |

### Audit a document corpus

Three read-only audits, each answering a different question. They diagnose and flag; they don't
rewrite (a `--fix` flag does mechanical-only repairs where offered).

| Skill | The question it answers |
|---|---|
| **consistency-audit** *(slash-only)* | Do the documents **agree**? Finds contradictions, drift, broken cross-references, and breaches of the corpus's own declared rules — within and between docs. Reports findings for the owner to adjudicate; does not pick a winner. |
| **epistemic-audit** *(slash-only)* | Is the model **complete and correct** as a description of the real subject? Reconstructs the implicit model, then attacks it from first principles — gaps, load-bearing assumptions, frame challenges. Not a consistency check. |
| **structural-audit** *(slash-only)* | Is the content **in the right place and well-layered**? Auto-detects mode: a directory → architecture audit (inter-document placement and boundaries); a file → document audit (intra-document readability/layering). Produces a concrete restructuring plan as a handoff for another agent to execute. |

### Engineer the instructions themselves

| Skill | What it does |
|---|---|
| **metaprompt-engineer** *(slash-only)* | A prompt engineer for **authoring or overhauling instruction artifacts** — skills, `AGENTS.md`, slash commands, system prompts. Turns your expectations into dense directives, hunting known instruction failure modes (sycophancy, bloat, phantom affordances, emphasis inflation, …) and shipping each load-bearing rule with a falsifier. **Use when** writing a new instruction artifact or fixing one that misbehaves; defaults to a full rebuild, surgical in evidence-driven Iterate passes (e.g. fed a `citation`). |
| **citation** *(slash-only)* | Records *how* an instruction artifact violated **its own rules** in real use — each breach backed by a verbatim quote — and writes a `CITATION_<artifact>.md`. Records evidence only; does not diagnose or rewrite. **Use to** gather the evidence that feeds metaprompt-engineer's Iterate pass. |

## How they fit together

- **attack-duck** develops an idea, then points you at implementation or at `report`/`handoff` to capture it.
- **handoff** briefs the next session; **report** records the outcome once the work is done.
- **handoff-edit** → **apply-edit** is its own author→receiver pair for changes to critical documents.
- **data-investigation** runs the probe loop, then closes out through `handoff` and `report`.
- **structural-audit** emits a restructuring plan that **apply-edit** can carry out.
- **citation** captures an artifact's failures; **metaprompt-engineer** rebuilds the artifact (these skills included).

## Structure

```
.claude-plugin/plugin.json        # makes the folder a skills-dir plugin (name: rkp)
.claude-plugin/marketplace.json   # lets others add it as a marketplace
skills/<name>/SKILL.md            # one folder per skill (auto-discovered)
```

## License

[MIT](LICENSE) © Robert Konklewski
