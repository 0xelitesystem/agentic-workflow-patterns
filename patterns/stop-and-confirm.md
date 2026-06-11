# Stop and confirm

## The pattern

Insert mandatory checkpoints in agent workflows where the agent must stop and wait for human confirmation before continuing. Use these for:

- Before writing code (after scoping)
- Before adding new dependencies
- Before modifying schema/migrations
- Before touching security-relevant code
- Before deleting anything substantial

## How to enforce it

In the prompt:

```
Before [action]:
1. Describe what you're about to do
2. List files that will change
3. STOP. Wait for me to say "go" before doing anything.
```

The "STOP" line in caps is more effective than polite phrasing. Agents respect explicit stop signals more than implicit ones.

## Why this matters

The biggest agent failures aren't bad code, they're correct code in the wrong place, or correct intent applied destructively. A 30-second human checkpoint at the right moment prevents an hour of cleanup.

## When NOT to use this

For trivial tasks (rename a variable, fix a typo), the checkpoint is more friction than value. Save it for tasks where the agent's choices have non-obvious consequences.

## Variation: dual confirmation

For very destructive actions (deleting files, dropping tables, force-pushing), require TWO confirmations spaced apart:

```
Before [destructive action]:
1. Describe what's about to happen
2. List exactly what will be destroyed
3. Wait for "go ahead"
4. Show me the command you're about to run
5. Wait for "yes, run it"
```

The second confirmation prevents "yes, do that" from being interpreted more aggressively than intended.
