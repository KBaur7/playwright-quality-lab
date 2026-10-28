# ADR-0001: TypeScript and Playwright

**Status:** Accepted, October 2026

## Context

The suite needs one language and one framework covering browser and API testing, with
good support for parallel execution and failure diagnosis.

## Decision

TypeScript with Playwright Test for both UI and API tests.

## Rationale

- Auto-waiting and web-first assertions remove the most common source of flaky UI tests:
  fixed sleeps.
- UI and API tests share one runner, one reporter and one fixture model, so setup and
  teardown are not duplicated across two tools.
- Traces capture a full timeline, DOM snapshots and network activity for a failed run,
  which makes intermittent failures diagnosable after the fact rather than only
  reproducible locally.
- TypeScript's types catch malformed test data and wrong response shapes at compile time.
- Playwright roles are listed with TypeScript in the large majority of postings that
  mention the framework, so the combination is portable across teams.

## Trade-offs

- Selenium with Java still carries the highest posting volume, particularly in large
  enterprises. A second language binding can be added later if a target stack requires it.
- TypeScript adds a compile step that plain JavaScript would not. The cost is accepted in
  exchange for earlier feedback.

## Revisit if

The system under test or the owning team standardises on a Java or Python stack.
