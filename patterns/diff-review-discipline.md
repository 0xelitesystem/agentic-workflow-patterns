# Diff review discipline

## The pattern

Read every line of every diff before merging. No exceptions for "trivial" changes.

When reading:

- Verify each change matches what was asked
- Look for changes that weren't asked (scope creep)
- Look for additions (new dependencies, new files, new exports)
- Look for deletions (especially security checks, error handling, tests)
- Look for "while we're here" cleanups
- Read the test changes specifically, fake tests show up here

## Why this matters

The agent's summary of what it did is always optimistic. The diff is ground truth. If you only read the summary, you'll merge things you didn't intend to.

## What to flag specifically

**In additions:**
- New dependencies
- New files (especially generated-looking ones)
- Comments that weren't asked for
- Logging statements
- Try/catch wraps
- "Improvements" to nearby code

**In deletions:**
- Tests being removed (instead of updated)
- Validation being relaxed
- Comments being stripped
- "Unused" code (verify it's actually unused)

**In modifications:**
- Renames that affect more files than expected
- Type changes (especially `any` / `unknown` / `Object` widening)
- Behavior changes claimed to be "no behavior change"

## Tools that help

- `git diff --stat` for the file count and line count overview
- [agent-diff-reviewer](https://github.com/0xelitesystem/agent-diff-reviewer) - browser tool for diff review with scary-changes detection
- IDE diff views with side-by-side comparison
- Code review tooling that highlights specific risky patterns

## When the diff is too big to review

That's a signal the task was too big. Push back:

- "This diff is 800 lines for what was supposed to be a small change. Can you break it into smaller commits?"
- Or: revert and re-scope into smaller tasks.
