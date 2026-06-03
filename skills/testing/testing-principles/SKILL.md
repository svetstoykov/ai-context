---
name: testing-principles
description: Use when writing, reviewing, or structuring automated tests, including unit, integration, end-to-end, contract, and regression tests.
---

# Testing Principles

## Purpose

Write tests that prove behavior through observable outcomes, fail for useful reasons, and stay reliable across local development and CI.

## When To Use

Use this skill when the user asks to:

- write or add tests
- review test code
- choose between unit, integration, and end-to-end coverage
- fix brittle, flaky, or hard-to-maintain tests
- define a testing strategy for a feature or bug fix

## Core Principles

- **Arrange, Act, Assert:** every test has clear setup, one action, and assertions on the observable result.
- **One behavior per test:** each test should have one reason to fail and a name that explains the scenario and expected outcome.
- **Test behavior, not implementation:** assert public contracts and externally visible results instead of private mechanics.
- **Control nondeterminism:** isolate time, randomness, concurrency, network calls, file I/O, and external services.
- **Use meaningful failures:** write assertions and names that make failures actionable.
- **Keep tests maintainable:** reduce noisy setup with builders, fixtures, or helpers only when they clarify intent.

## Layer Selection

| Layer | Use For | Avoid Using For |
|---|---|---|
| Unit | Pure logic, validation, algorithms, local decisions, edge cases | Verifying framework wiring or multi-component orchestration |
| Integration | Components interacting through real boundaries, persistence, serialization, dependency wiring | Exhaustive edge cases that are cheaper as unit tests |
| End-to-end | Critical user or system workflows through production-like boundaries | Broad combinatorial coverage or routine logic checks |
| Contract | Shared interfaces, interchangeable implementations, provider/consumer expectations | Behavior unique to a single implementation |
| Regression | Reproducing a specific bug before fixing it | Replacing broader behavior coverage |

## Test Design Rules

### Names

- State the behavior and expected result.
- Prefer names like `Rejects_empty_email_address` over `Test1` or `Validation_works`.
- If a test name needs "and", consider splitting the test.

### Arrange

- Keep setup focused on what the behavior needs.
- Use builders for complex object graphs.
- Avoid duplicating large setup blocks across tests.
- Prefer deterministic fakes over live dependencies unless the test layer intentionally crosses that boundary.

### Act

- Perform one primary action.
- Do not combine multiple behaviors in one test.
- Capture the result through the public API.

### Assert

- Assert observable outcomes.
- Assert state, return values, emitted events, persisted data, or user-visible effects as appropriate.
- Avoid asserting private call counts or incidental implementation details unless interaction is the public contract.

## External Dependencies

- Unit tests should not require network access, secrets, wall-clock timing, or live services.
- Integration tests may use real local dependencies when they are deterministic and cheap to start.
- End-to-end tests that require live services or paid APIs must be opt-in and skipped by default when credentials are absent.
- Skips must protect optional runtime requirements, not hide broken behavior.

## AI-Agent And LLM Workflows

For agent or LLM-powered systems, keep most tests deterministic by using fixtures, recorded responses, local fakes, or contract tests around provider adapters.

Use live LLM calls only for critical end-to-end confidence checks. Gate those tests behind explicit configuration, document required environment variables, and avoid running them in standard CI unless the project intentionally supports that cost and variability.

## Review Checklist

- The test name describes the behavior and expected result.
- The test has clear Arrange, Act, and Assert phases.
- The test asserts public behavior instead of private mechanics.
- Nondeterministic dependencies are controlled.
- The test would fail if the behavior regressed.
- The failure message would help diagnose the problem.
- The selected test layer matches the risk and scope.
