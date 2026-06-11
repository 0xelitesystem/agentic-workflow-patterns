# Going in circles on a bug

## When this happens

- 30+ minutes of agent attempts, no progress
- Multiple agent sessions, each restating the bug, each failing
- The bug feels like it should be simple but isn't being solved

## What to do

Take over manually. Specifically:

1. **Stop using the agent for this.** Open an editor.
2. **Write down what you actually know.** Not what the agent thinks; what you have evidence for.
3. **Reproduce the bug yourself.** Step through it in a debugger if needed.
4. **Form your own hypothesis.** Test it.

If you reach a fix manually, optionally use the agent for the cleanup (writing tests, refactoring the fix). But the diagnosis was yours.

## Why this matters

Agents struggle with problems that require actually reading values at runtime, stepping through state changes, or noticing what's NOT in the code. The kinds of bugs that turn into circles are usually the kinds that need a human in the debugger.

## When to suspect this is happening

- The agent keeps proposing things that fail in similar ways
- Each fix introduces a new failure
- The agent says "this should work" repeatedly and it doesn't
- The bug involves timing, concurrency, or state that the agent can't observe

## After you fix it

Update CLAUDE.md (or your team's lessons-learned doc) with:
- The bug
- Why agents got it wrong
- What clues should have pointed to the real cause

Future-you (or future-agents in the same project) will benefit.

## Variation: pair the agent with you

Instead of full handover, pair: you debug interactively, telling the agent what you see at each step. The agent helps with the parts it's good at (proposing tests, formulating fixes, writing the change) while you drive the diagnosis.
