# Repository conventions

Conventions for anyone, human or assistant, contributing to this suite.

## Test code

- No fixed waits. Express waiting through web-first assertions that retry.
- Locators: `getByRole` with an accessible name, or a stable `data-testid`. Never DOM
  position or generated class names.
- Each test creates the data it needs and passes in parallel and in any order.
- An assertion must fail when the behaviour it covers breaks. Verify by breaking it.
- Prefer the cheapest level that can cover a risk. Use the UI only where the UI is the risk.

## Review

Every test entering `tests/` is reviewed against `docs/ai-review-checklist.md`,
whoever or whatever wrote it. See `docs/decisions/0003-ai-assisted-tests.md`.

## Documentation

- A significant technical choice gets a decision record in `docs/decisions/`, including
  its trade-offs.
- A flaky failure gets an entry in `docs/flaky-log.md` with its root cause and fix.
- Status tables in `README.md` reflect merged work only.
