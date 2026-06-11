# Verify by running

## The pattern

After the agent says it's done, don't trust the agent. Run the code.

For code: `npm test`, `cargo test`, `pytest`, `go test`.
For builds: `npm run build`, `cargo build`, `make`.
For migrations: apply to a test database.
For configs: `kubectl apply --dry-run=client`, `terraform plan`, `helm lint`.

The agent is allowed to think the work is done. You're not allowed to think so until something runs.

## Why this matters

Most agent failures are caught by running. Hallucinated APIs fail to import. Type-correct nonsense crashes. Tests that don't test reveal themselves under mutation. Configs with wrong keys fail validation.

The agent doesn't run code by default in many tools. You do.

## What "running" means by code type

| Code type | What to run |
|---|---|
| Functions / classes | Unit tests for those functions |
| Endpoints | Send a real HTTP request |
| Migrations | Apply forward, then backward, on test DB |
| CLI tools | Invoke with realistic args |
| Configs | Tool's validate / dry-run |
| Frontend | Build + manual smoke test in browser |
| Library code | Import and call from a test |

## What NOT to verify-by-running

- Code that requires production credentials (verify in staging)
- Destructive code (extra paranoia: dry-run, code review, then run on isolated env)
- Code that can't be cheaply rolled back

## Variation: continuous verification

Set up automation that runs the verification on every agent commit:

- Pre-commit hooks for fast checks (lint, type-check)
- CI for full test suite
- Preview environments for endpoint changes

The shorter the loop from agent change to verification result, the faster you catch issues.
