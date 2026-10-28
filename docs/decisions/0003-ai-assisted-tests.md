# ADR-0003: Standards for AI-assisted tests

**Status:** Accepted, October 2026

## Context

AI assistants generate test code quickly, and much of it passes. Passing is not the bar:
a generated test can assert the wrong thing, assert nothing meaningful, depend on state
another test owns, or lock in a brittle locator. Such a test reports green while covering
nothing, which is worse than no test at all because it suppresses the signal.

## Decision

Generated test code is treated as an untrusted contribution and reviewed before it enters
the suite.

Every test entering `tests/` is reviewed against the checklist in
[`docs/ai-review-checklist.md`](../ai-review-checklist.md), regardless of origin:

- The assertion fails when the behaviour it covers breaks.
- No fixed waits; waiting is expressed through web-first assertions.
- The test owns its data and passes in parallel and in any order.
- Locators are tied to accessible roles or stable test ids, not DOM position or
  generated class names.
- The failure message identifies the cause without a rerun.

Configuration (CI workflows, Playwright config) may be generated, and is reviewed line by
line before it is committed.

## Consequences

- Review time is spent per test rather than per batch.
- Every test in the suite has an owner who can explain why it passes and what would make
  it fail.
