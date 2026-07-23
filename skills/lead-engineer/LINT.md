# Fresh-eyes lint charges

Recipe: fill `<FILES>` (the files the build changed), `<DIFF>` (the build's diff, saved to a
file). The agent gets nothing else — never this chat's Ledger, plan, or reasoning. Runs, low
effort, sonnet-class — counts fixed, a small diff does not shrink the panel: **two** of the rent
charge, **one** of the baseline charge; union all flags.

<!-- Counts benchmarked: rent recall saturates at one run (4/4) and errs quiet, so a second run
buys union insurance cheaply; baseline recall also saturates at one run (3/3 core) but the charge
surfaces more grounded style flags, so it runs once to bound adjudication load. See
docs/REPORT_lead-engineer-iterate-2026-07-23.md. -->

## Rent charge

Benchmarked — an edit below voids that validation.

---

You are a fresh-eyes reviewer of a code change. You have NO access to the session that wrote it
— judge only what you read.

Read the files `<FILES>` fully, then the diff at `<DIFF>`. Judge ONLY the lines the diff ADDS.
Every added word costs a future reader attention; it survives only by carrying something the
code itself cannot.

Flag each added comment, docstring, or constant that is:

(a) restatement — it respells the identifier it sits on, its parameters, or its type, adding no
fact absent from the signature.

(b) narration — it describes what the following line or block does, rather than why, under what
contract, or at what risk.

(c) single-use constant — a named module-level constant referenced exactly once, as a parameter
default. Its value belongs at the use site.

Do NOT flag: a comment carrying a unit, an invariant, a boundary condition, a non-obvious
rationale, a gotcha, or a pointer to an external spec — these are the reasons comments exist.
Do NOT flag a short comment on a member whose sibling members all carry comments: matching the
file's existing form is legitimate, even where the text is thin. Do NOT flag code, only prose
and named constants.

For each flag: quote roughly its first 12 words, name the file and the enclosing function or
type, give the class (restatement / narration / single-use constant) and the cheapest fix.

## Baseline charge

Benchmarked — an edit below voids that validation.

---

You are a fresh-eyes reviewer of a code change. You have NO access to the session that wrote it
— judge only what you read.

Read the files `<FILES>` fully, then the diff at `<DIFF>`. The file's existing contents are the
style authority; the change must read as if the file's author wrote it.

Flag each element the diff ADDS that has no sibling of its kind in the file it landed in:

(a) orphan construct — a form the file does not otherwise use: a module-level constant where
every other threshold is an inline parameter default, an import or typing style unlike the
file's, an abstraction level (a helper class, a registry, a factory) with no counterpart.

(b) odd member out — a new member of a type, enum, or config block whose existing members all
share a form the new one breaks: bare where the others are annotated, annotated where the
others are bare, a naming pattern that does not follow.

**Ground every flag in a sibling you can quote.** Name the specific existing line that
establishes the convention the addition breaks, and quote it. If you cannot point to one, the
file has no convention here — do not flag it. General style preference is not a finding.

For each flag: quote the added element, quote the sibling line establishing the convention, name
the class (orphan construct / odd member out) and the cheapest fix.
