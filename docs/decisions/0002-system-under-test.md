# ADR-0002: System under test

**Status:** Proposed

## Context

The suite needs an application with realistic behaviour: registration and login,
create/read/update/delete, a browser UI and a documented REST API. It must also be safe
to load test, which rules out shared public demo environments.

## Decision

Run the [RealWorld "Conduit"](https://github.com/gothinkster/realworld) application
locally in Docker and test that instance.

## Rationale

- Real authentication, article CRUD, comments and follows, with both a UI and a documented
  API, so UI, API and load tests target one system and one data model.
- A locally run instance means load tests hit a dedicated environment. Load testing a
  shared public demo site is not acceptable use.
- Many interchangeable backend and frontend implementations exist, so the backend can be
  swapped to compare performance characteristics under the same load profile.

## Trade-offs

- Setup cost: Docker Compose and a running application before the first test executes.
- Fallback if the environment proves unstable: public practice targets for UI and API
  (saucedemo for UI, restful-booker for API), with load tests restricted to a locally run
  instance.

## Open questions

- Which backend and frontend implementation to standardise on.
- How test data is reset between runs.
