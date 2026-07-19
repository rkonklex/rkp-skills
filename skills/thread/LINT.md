# Fresh-eyes lint charge

Recipe: two runs, sonnet-class model, low effort; union the flags. Fill `<FILE>` (the record),
`<DIFF>` (the session's diff, saved to a file), `<SECTIONS>` (the sections this session
touched, at heading granularity). The agent gets nothing else — never this chat's findings.
The wording below is benchmarked — an edit here voids that validation.

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
