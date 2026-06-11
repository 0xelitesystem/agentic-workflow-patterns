# Hard constraints list

## The pattern

Before any non-trivial agent task, write down the hard constraints. Not the goal, the things that MUST NOT happen.

Example for a refactor task:
```
Hard constraints:
- External API behavior unchanged (same routes, same response shapes)
- No new dependencies in package.json
- Database schema unchanged
- Existing tests must still pass
- Change touches only files in src/auth/ and src/lib/auth-utils.ts
```

Paste this with every prompt. Rephrase to remind the agent if it strays.

## Why this matters

Agents drift. They optimize for "appearing helpful" which can include rewriting things you didn't ask for. Hard constraints are the boundary that says "no, even if you think it'd be helpful, don't."

The constraints work better when stated negatively ("must NOT do X") than positively ("must do Y"). Negative constraints are unambiguous; positive ones get interpreted creatively.

## What kinds of constraints to list

Common categories:

- **Scope** ("changes only files in X")
- **Behavior** ("inputs and outputs unchanged")
- **Dependencies** ("no new packages")
- **Performance** ("benchmark must not regress")
- **Compatibility** ("must work on Node 18+")
- **Security** ("must not log auth tokens")
- **Style** ("match existing patterns in src/")

## What NOT to put in constraints

- Things you actually want the agent to do (those go in the goal)
- Subjective things ("write clean code")
- Things you don't actually care about (don't pollute the list)

## Variation: project-level constraints in CLAUDE.md

Constraints that apply to ALL tasks in the project go in `CLAUDE.md` / `AGENTS.md`. Per-task constraints go in the prompt.
