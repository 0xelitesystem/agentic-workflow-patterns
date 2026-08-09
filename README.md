# agentic-workflow-patterns

Patterns for working with coding agents productively. How to scope work, validate output, recover from stuck agents, and know when to take over.

## Why this exists

The framing of "AI does the coding" hides the real work, which is everything around the coding: choosing what to delegate, structuring the delegation so the agent can succeed, validating that the work is actually done, and recovering when it isn't. These patterns codify what's working in practice.

## The patterns

### Scoping

- [right-sized-task.md](./patterns/right-sized-task.md), what an agent-sized task looks like
- [hard-constraints-list.md](./patterns/hard-constraints-list.md), communicating non-negotiables clearly
- [stop-and-confirm.md](./patterns/stop-and-confirm.md), forcing a checkpoint before code

### Running

- [single-loop-discipline.md](./patterns/single-loop-discipline.md), one task at a time, finished, then next
- [batch-then-review.md](./patterns/batch-then-review.md), when to let the agent run a sequence
- [shared-context-files.md](./patterns/shared-context-files.md), CLAUDE.md/AGENTS.md as evolving context

### Validating

- [verify-by-running.md](./patterns/verify-by-running.md), running > reading the code
- [adversarial-input-pass.md](./patterns/adversarial-input-pass.md), second pass with hostile inputs
- [diff-review-discipline.md](./patterns/diff-review-discipline.md), what to look for in agent diffs

### Recovering

- [agent-stuck-in-a-loop.md](./patterns/agent-stuck-in-a-loop.md), detecting and breaking out
- [going-in-circles-on-a-bug.md](./patterns/going-in-circles-on-a-bug.md), when to take over manually
- [reset-the-context.md](./patterns/reset-the-context.md), when context window has poisoned the conversation

### Knowing when not to

- [tasks-not-to-delegate.md](./patterns/tasks-not-to-delegate.md), what shouldn't go to an agent at all
- [time-to-take-over.md](./patterns/time-to-take-over.md), recognizing when AI is no longer adding value

## How to use

- Read once to calibrate
- Reference when something feels off in your workflow
- Cite to teammates: "this is the [going-in-circles-on-a-bug] pattern"

## Contribute

PRs welcome. See [CONTRIBUTING.md](./CONTRIBUTING.md). Patterns must come from real experience and address a specific situation.

## More

Part of a catalog of single-file browser tools and plain-language references, all MIT licensed and dependency-free: [0xelitesystem.github.io](https://0xelitesystem.github.io/). Built by [elitesystem.ai](https://elitesystem.ai).

## License

MIT.

## Related

- [ai-coding-prompt-recipes](https://github.com/0xelitesystem/ai-coding-prompt-recipes)
- [vibe-coding-anti-patterns](https://github.com/0xelitesystem/vibe-coding-anti-patterns)
- [ai-generated-code-review-rubrics](https://github.com/0xelitesystem/ai-generated-code-review-rubrics)
