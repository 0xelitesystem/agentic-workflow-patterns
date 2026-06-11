# Batch then review

## The pattern

Some tasks are mechanical: apply the same change across N similar files. Migrating from one library to another. Adding a header comment to all source files. Fixing a deprecated API across the codebase.

For these, batching is appropriate:

```
Apply this change to every file matching pattern X:
- [exact change description]

For each file:
- Skip if not applicable (and tell me why)
- Apply if applicable
- Note any case where the change isn't trivial

After processing all files, give me:
- List of files changed
- List of files skipped (with reason)
- List of files that need manual review
```

## When to use

- The change is mechanical (find + replace, mostly)
- The pattern is well-defined
- Verification is feasible across the batch (tests, linter, build)
- Each file's change doesn't depend on the others

## When NOT to use

- The change requires per-file judgment ("update each file's structure")
- The change is risky (touch security code, schema, payment logic)
- Verification across the batch isn't feasible

## Why this matters

Batching is efficient for the right kind of task. The risk is missing per-file edge cases that would warrant a one-off decision. The mitigation: explicit "needs manual review" output, plus running tests after the batch.

## Variation: incremental batching

For very large batches (100+ files), do them in tranches:

- Tranche 1: 10 files
- Verify
- Tranche 2: 50 files
- Verify
- Tranche 3: rest

This catches systematic mistakes early instead of after 200 files have been changed.
