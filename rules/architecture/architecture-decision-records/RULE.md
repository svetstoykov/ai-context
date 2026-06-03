# Architecture Decision Records

When you make or propose a significant architectural change, create an Architecture Decision Record before or alongside the implementation.

## What Triggers An ADR

- Adding or replacing a dependency, library, framework, or platform service.
- Choosing an authentication, authorization, or permissions approach.
- Defining a data model, schema, storage model, or database design.
- Establishing an API contract, event contract, or integration pattern.
- Making a performance tradeoff such as caching, queuing, batching, or denormalization.
- Choosing a deployment, infrastructure, hosting, or runtime pattern.
- Creating a long-lived convention that future contributors must follow.

## ADR Location

Create ADR files at:

```text
docs/adr/YYYY-MM-DD-short-decision-title.md
```

If the repository already has a different ADR directory or naming convention, follow the existing convention.

## ADR Format

```markdown
# ADR: [Short descriptive title]

**Date:** YYYY-MM-DD
**Status:** Proposed | Accepted | Deprecated | Superseded
**Revisit when:** [Specific condition or date]

## Context

What problem was being solved? What constraints or forces shaped this decision?

## Decision

What was chosen? Why this option over the alternatives?

## Alternatives Considered

What else was evaluated, and why was it rejected?

## Consequences

What is gained? What tradeoffs, costs, or risks were accepted?
```

## Rules

- Create one ADR per decision.
- Keep each section concise, usually 2 to 4 sentences.
- Always include `Revisit when`; every decision needs a review trigger.
- Use `Proposed` for decisions not yet accepted.
- Use `Accepted` when the decision is current policy.
- If a decision is later reversed, update its status to `Superseded` and link to the replacement ADR.
- Do not delete old ADRs. Superseded decisions are still part of the project history.
