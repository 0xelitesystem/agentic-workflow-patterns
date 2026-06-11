# Single-loop discipline

## The pattern

One task at a time. Finished. Verified. Then the next.

Don't:
- Stack three tasks: "do X, then Y, then Z"
- Mix exploration and execution: "look around, then do X"
- Run an open-ended loop: "keep improving things until I tell you to stop"

Do:
- One task with a clear definition of done
- Verify done before next
- Then explicitly start the next task

## Why this matters

Compounding failures. If task X fails subtly and you queued Y and Z, you're now debugging across three changes. If X is verified before Y starts, problems are localized.

Also: agent attention. Long sequential plans dilute focus. The agent does worse work on item 5 of a list than on the same item as a focused single ask.

## What single-loop discipline looks like in practice

```
You: [scoped task X]
Agent: [does X]
You: [verify X works]
You: [scoped task Y]
Agent: [does Y]
You: [verify Y works]
...
```

vs the anti-pattern:

```
You: do X, then Y, then Z, and let me know when all three are done
Agent: [does some confused mix of X, Y, Z over 30 minutes]
You: [now what's broken? hard to tell]
```

## Exceptions: when batching is OK

See [batch-then-review.md](./batch-then-review.md). Some tasks are genuinely sequential mechanical operations (e.g. apply the same migration to 12 files). Those can batch. But mixed-domain tasks shouldn't.
