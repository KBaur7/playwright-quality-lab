# Test review checklist

Applied to every test entering the suite. See
[ADR-0003](decisions/0003-ai-assisted-tests.md).

## Assertions

- [ ] The assertion fails if the behaviour under test breaks. Verified by breaking it.
- [ ] Asserts on observable behaviour, not on implementation detail.
- [ ] No assertion that passes on an empty, null or default value.

## Waiting

- [ ] No `waitForTimeout` or other fixed sleep.
- [ ] Waiting is expressed through web-first assertions that retry.
- [ ] No `await` missing on a Playwright call.

## Isolation

- [ ] The test creates the data it needs and does not depend on another test's state.
- [ ] Passes when run alone, in parallel and in reverse order.
- [ ] Cleans up, or targets data scoped to the run.

## Locators

- [ ] Role-based or stable test id, never DOM position or generated class names.
- [ ] Resolves to exactly one element.

## Diagnosability

- [ ] The failure output identifies the cause without rerunning the test.
- [ ] Trace and screenshot retained on failure.

## Value

- [ ] Covers a risk named in the test strategy.
- [ ] Sits at the cheapest level that can cover it; UI only where the UI is the risk.
- [ ] Not a duplicate of existing coverage.
