# Right-sized task

## The pattern

A task is the right size for an agent if you can:

1. State the goal in one sentence
2. List the files involved (or it's clear from the goal)
3. Verify the result in under a minute

If any of those is hard, the task is too big or too vague.

## Examples

**Right-sized:**
- "Add a `--verbose` flag to the CLI that prints the parsed config before running."
- "Extract the duplicated date-parsing logic in `report.ts` and `analytics.ts` into a single utility."
- "Rename `getUser` to `loadUser` and update all callers."

**Too big:**
- "Refactor the auth module."
- "Make the app faster."
- "Add user accounts."

**Too vague:**
- "Fix the bug."
- "Improve the code."
- "Make this better."

## Why this matters

Agents work best on bounded problems where success is verifiable. Open-ended tasks lead to scope creep and confident-wrong direction. The handoff to the agent should be a sentence, not a meeting.

## How to right-size a too-big task

Break it down before delegating:

- "Refactor the auth module" -> first decompose into 5-7 specific changes, each right-sized.
- "Add user accounts" -> first decompose into: schema, registration endpoint, login endpoint, session handling, UI form.

Then delegate the right-sized pieces one at a time.

## How to right-size a too-vague task

Add specifics until you can write the verification:

- "Fix the bug" -> "Fix the bug where uploading a file >5MB returns a 500 instead of a friendly error."
- "Make this better" -> "Reduce the time to first paint on the homepage by removing render-blocking CSS imports."
