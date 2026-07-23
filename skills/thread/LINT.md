# Fresh-eyes lint charges

Recipe: fill `<FILE>` (the record), `<DIFF>` (the session's diff, saved to a file), `<SECTIONS>`
(the sections this session touched, at heading granularity). The agent gets nothing else — never
this chat's findings. Runs, low effort, sonnet-class — counts fixed, a small diff does not
shrink the panel: **two** of the narration/cold charge, **one** of the economy charge; union
all flags.

## Narration/cold charge

Benchmarked — an edit below voids that validation.

---

You are a fresh-eyes reviewer of a long-running research record. You have NO access to the
session that edited it — judge only what you read.

Read the file `<FILE>` fully. Then read the last session's diff at `<DIFF>`. It shows what
that session changed. Judge the RESULT — the current file text; use the diff only to locate
changed text and to notice references to old-state content, not to evaluate the edit process.

The record's contract: live sections state current knowledge as if written today; narrative
history — what changed, what an earlier version said, what got corrected or superseded —
belongs ONLY in the Session log.

Check ONLY these sections: `<SECTIONS>`.

Flag every sentence, heading, or table cell in those sections that violates either:

(a) narration — it narrates change instead of stating current state: it references an earlier
version's content or values ("supersedes", "retracted", "re-measured", "now X", "still X",
"grown to", "was A now B", "earlier", "no longer"), or is only informative to a reader who
already knows the old state. A bracketed provenance stamp naming evidence (e.g. "[measured,
P6 2026-07-19]") is NOT a violation.

(b) cold — it cannot be understood without the session that wrote it, or it contradicts other
parts of the file (undefined shorthand, dangling references, stale internal contradictions).

Do not flag anything inside the Session log. Quote each flagged item (roughly its first 15
words), name its section, give its class (narration or cold) and a one-line reason.

## Economy charge

Benchmarked — an edit below voids that validation.

---

You are a fresh-eyes reviewer of additions to a long-running research record. You have NO
access to the session that wrote them — judge only what you read.

Read the file `<FILE>` fully, then the last session's diff at `<DIFF>`. Judge ONLY the lines
the diff ADDS. The record is read cold by every future session, so every added sentence must
earn its place.

Flag each added sentence, list item, or table row that is:

(a) duplicate — it restates a fact, number, instruction, or definition that already has a home
elsewhere in the file (including another line this same diff adds). A short pointer to the
home is fine; a restatement is not. Name the other home.

(b) over-grain — it sits in the Session log, the Work tracker, or a Status paragraph and runs
past that section's grain: log and tracker entries are a few lines stating what changed or
what resolves it, and detail belongs in the finding they point to. Do NOT apply this class
inside Findings sections — measured working detail there is legitimate.

(c) no-claim — it adds nothing a future session could act on: process narration, restated
context, a sentence whose deletion loses no information.

(d) malformed tag — a bracketed origin tag whose bracketed content is not built from the
record's declared tag set (the contract block at the top of the file declares the set): it
contains free-text words, qualifiers, or ratings that are not declared members. A compound
of declared members, and an evidence stamp appending a probe id and/or date to a declared
member, are NOT violations.

For each flag: quote roughly its first 15 words, name its section, give the class (duplicate /
over-grain / no-claim / malformed tag) and the cheapest fix — cut, point at the existing home,
or restate the tag from declared members. Do not flag provenance stamps, status lines, or
terse technical claims merely for being dense.
