# Reset the context

## When to do it

Long agent sessions accumulate context that becomes counterproductive:

- Failed attempts the agent now references confidently
- Misunderstandings that have compounded across messages
- Stale code state in the agent's mental model
- The agent has "decided" something that's wrong and won't revisit

When the agent's confidence stops being earned by recent reality, reset.

## How to reset

1. **End the current session.**
2. **Capture what you learned.** Specifically:
   - What worked from the session
   - What didn't, and why (so you don't try it again)
   - What's actually committed vs what was attempted
3. **Start a fresh session.**
4. **Bring forward only what's relevant.** A summary, not the full transcript.
5. **Fresh prompt with the current state.**

## What "current state" means in the new session

Don't say "continuing from before, please finish X." Say:

- Where the code currently is
- What's done
- What's left
- What we tried that didn't work (so the new agent doesn't repeat it)
- The next concrete step

Treat the new session as if it's the first contact, because for the agent, it is.

## When NOT to reset

- The agent is making progress, even slowly
- Context has useful working memory (e.g. mid-debugging session with relevant clues)
- Resetting would lose more than it gains

## Tools that help

- Some agents have explicit "summarize and clear" commands
- Others let you start a new session with a system prompt that includes context

## Why this matters

The longer a session runs, the more anchored the agent is to its existing model. Sometimes that's good (working memory). Often it's bad (compounded errors). Resetting is the cheapest way to break out.
