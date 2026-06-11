# Shared context files (CLAUDE.md / AGENTS.md)

## The pattern

Maintain a per-project markdown file that captures the things every agent session needs to know:

- Project description (one paragraph)
- Build / test / run commands
- Codebase structure (where things live)
- Conventions (style, naming, patterns)
- Things that broke before (specific past failures)
- Constraints that apply project-wide

Different tools call this different things:
- Claude Code: `CLAUDE.md`
- Cursor / general: `.cursorrules` or `AGENTS.md`
- Aider: `.aider.conf.yml` or system prompt files

The format varies but the function is the same.

## Why this matters

The alternative is repeating context in every prompt. The shared context file is the agent's working memory across sessions.

## What goes in

**Highest value:**
- Build commands (`npm run build`, `cargo test`, etc.)
- Test commands
- Specific past failures: "We tried X, it didn't work because Y. Don't try X again."
- Project conventions that aren't obvious from reading the code
- "Always use" / "Never use" lists for libraries

**Medium value:**
- Architecture overview (when project is non-trivial)
- Naming conventions
- Where utilities live

**Low value or harmful:**
- Generic coding advice ("write clean code")
- Detailed style rules better left to a linter
- Aspirational descriptions ("we are building the best X")

## How to grow it

Update the file when:

- An agent makes a mistake the file would have prevented (add a constraint)
- A pattern becomes the team norm (document it)
- A library/version changes (update the version-pin entries)

Don't update it for one-off corrections. Things that go in the file must apply to ALL future tasks.

## Variation: per-directory CONTRIBUTING.md

For monorepos, each subdirectory can have its own context file. The agent reads the relevant one based on which area it's working in.

## Tools

- [claude-md-generator](https://github.com/0xelitesystem/claude-md-generator) - interactive builder
- [cursor-rules-collection](https://github.com/0xelitesystem/cursor-rules-collection) - examples by stack
