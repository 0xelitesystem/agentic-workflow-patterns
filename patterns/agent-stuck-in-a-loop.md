# Agent stuck in a loop

## What it looks like

The agent makes a change. Tests fail. It makes another change. Tests fail differently. It reverts. Tests fail like the first time. It tries change #1 again. You watch this happen and realize it's been 20 minutes and 5 attempts and the bug is still there.

## Why agents loop

- The agent's mental model of the bug is wrong, but each attempt looks plausible
- The agent has tried things in isolation but hasn't synthesized the failures
- Context window has filled with attempt history that's now contradictory

## Detection

- Same set of files modified repeatedly
- Same test failing with different error messages each time
- Agent's narrative shifts ("oh, the issue is X" -> "actually Y" -> "actually X again")
- More than 3 attempts without convergence

## How to break out

1. **Stop the agent.** Don't let it keep churning.
2. **Reset.** New session, fresh context.
3. **Re-frame the problem.** "We've tried X, Y, Z and none worked. Here's what we observed: [specific outputs]. Don't propose a fix yet, what does this evidence actually tell us about the root cause?"
4. **Be explicit about what NOT to try.** "Don't propose any of: [list of attempts]. Anything else."
5. **If still stuck, take over manually.** See [going-in-circles-on-a-bug.md](./going-in-circles-on-a-bug.md).

## Prevention

- Set a max-attempts budget mentally ("agent gets 3 attempts, then I take over")
- Insist on explicit hypotheses before each attempt ("what's your theory of the bug? what would prove or disprove it?")
- Keep the agent's context lean, long failed-attempt history poisons new attempts
