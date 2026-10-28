# Playwright Quality Lab

<!-- Enable once CI is in place:
![Tests](https://github.com/<your-username>/playwright-quality-lab/actions/workflows/tests.yml/badge.svg) -->

End-to-end quality suite for the [RealWorld "Conduit"](https://github.com/gothinkster/realworld)
application: UI and API tests in TypeScript with Playwright, load tests with k6, running in CI.

The application under test is a Medium-style blogging platform with authentication,
article CRUD, comments and follows. It runs locally in Docker, so load tests target a
dedicated instance rather than a shared demo environment.

## Scope

| Area | Location | Status |
|---|---|---|
| UI tests: role-based locators, web-first assertions | `tests/ui/` | planned |
| API tests: status codes, response bodies, schema validation | `tests/api/` | planned |
| Fixtures, per-test data isolation, parallel execution | `tests/fixtures/` | planned |
| BDD scenarios for the core authoring and auth flows | `tests/features/` | planned |
| CI on every push, HTML report and traces as artifacts | `.github/workflows/` | planned |
| Load and stress tests with threshold enforcement | `perf/` | planned |
| Risk-based test strategy | [`docs/test-strategy.md`](docs/test-strategy.md) | planned |

## Tech stack

| Concern | Choice |
|---|---|
| Language | TypeScript |
| UI and API testing | Playwright Test |
| Load testing | k6, with JMeter for comparison |
| CI | GitHub Actions |
| Environment | Docker Compose |

## Getting started

Documented once the first suite lands.

## Project structure

```
docs/            test strategy, design decisions, flaky-test log
tests/ui/        browser tests
tests/api/       API tests
tests/fixtures/  shared setup and test data factories
tests/features/  BDD scenarios
perf/            k6 and JMeter scripts and reports
.github/         CI workflows
```

## Design decisions

Significant choices are recorded as decision records with their trade-offs:

- [ADR-0001: TypeScript and Playwright](docs/decisions/0001-typescript-playwright.md)
- [ADR-0002: System under test](docs/decisions/0002-system-under-test.md)
- [ADR-0003: Standards for AI-assisted tests](docs/decisions/0003-ai-assisted-tests.md)

## Reliability

Flaky failures are treated as defects in the suite. Each one is diagnosed from its
Playwright trace and recorded with its root cause and fix in
[`docs/flaky-log.md`](docs/flaky-log.md).

## Findings

Defects and risks surfaced by the suite:

| Finding | How it surfaced | Reference |
|---|---|---|
| | | |

## License

MIT
