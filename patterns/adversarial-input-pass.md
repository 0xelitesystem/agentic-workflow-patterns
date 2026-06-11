# Adversarial input pass

## The pattern

After verifying the code does what the agent claims, do a second pass with hostile inputs. The agent tested the happy path. You test the unhappy paths.

Cases to try:

- Empty inputs (empty string, empty array, null, undefined)
- Very large inputs (10MB string, 1M element array)
- Malformed inputs (bad JSON, invalid encoding)
- Boundary values (max int, min int, zero, negative)
- Unicode (emoji, RTL text, combining characters, zero-width chars)
- Concurrent calls (race conditions)
- Slow / failing dependencies (timeout, 500 response)
- Inputs with control characters or escape sequences

## Why this matters

Agents test what they expect. Production hits what nobody expected. The adversarial pass closes the gap.

## How to make it efficient

Don't manually try 20 cases each time. Build a small library:

```python
# tests/fixtures/adversarial.py
EMPTY_INPUTS = ["", None, [], {}, 0, False]
LARGE_INPUTS = ["a" * 1_000_000, list(range(100_000))]
UNICODE_INPUTS = ["test", "\u65e5\u672c\u8a9e"  # CJK chars, "\U0001f680"  # emoji codepoint, "\u05d0" + "\u0300", "a\u200bb"]
MALFORMED_JSON = ['{"key":', '{"key": value}', '{"trailing":,}']
```

Then use these fixtures in property tests across modules.

## When the agent's code fails on adversarial input

The fix isn't always "make it work for that input." Sometimes the right answer is:

- Reject malformed input explicitly with a clear error
- Document the supported input space
- Add validation at the boundary

Don't let the agent silently expand support to handle inputs you don't actually want to support.
