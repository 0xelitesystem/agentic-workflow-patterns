# Time to take over

## Signs

- You've spent more time managing the agent than you would have spent doing it yourself
- Your prompts are getting longer to compensate for the agent's mistakes
- You're correcting the same kind of mistake repeatedly
- Verification is taking longer than the implementation would have
- The agent's output quality is declining as the session continues

## Recognizing the threshold

A useful heuristic: if you wouldn't accept this work product from a human collaborator at the same level of effort, why are you accepting it from the agent?

## What "taking over" looks like

You don't have to be all-in or all-out:

- **Hybrid**: write the structure yourself, let the agent fill in known patterns
- **Reviewer mode**: the agent proposes, you decide which parts to keep
- **Manual**: do it yourself; come back to AI for the next task

Each is appropriate at different times. Don't feel obligated to use AI when it's slowing you down.

## Why this matters

The promise of AI coding tools is faster work. If they're not delivering that for the current task, using them anyway is sunk-cost reasoning. Switch back to manual mode and ship.

## Don't blame the tool prematurely

Before deciding to take over, check:

- Was the task right-sized? ([right-sized-task.md](./right-sized-task.md))
- Were constraints clear? ([hard-constraints-list.md](./hard-constraints-list.md))
- Has context become poisoned? ([reset-the-context.md](./reset-the-context.md))

Sometimes a fresh session with better framing solves what looked like agent incompetence.

## When you take over, share the lesson

Update CLAUDE.md or notes with what you learned. The categories of tasks where you take over manually become a useful map: "agent does fine on X but not on Y."

This map evolves as agents improve. Re-test occasionally; capabilities have changed.
