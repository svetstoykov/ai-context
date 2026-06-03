---
name: task-writing
description: Use when creating development tasks, tickets, work items, backlog entries, or implementation-ready task descriptions from a feature, bug, or change request.
---

# Task Writing

## Purpose

Create development tasks that are precise enough for a developer or coding agent to execute without guessing. A good task defines scope, acceptance criteria, expected outcome, dependencies, and useful implementation notes.

This skill covers task creation only. Do not write implementation code unless the user separately asks for implementation.

## When To Use

Use this skill when the user asks to:

- create a task or ticket
- define work items
- plan a feature
- break down work
- formalize a change request
- turn discussion into backlog items

## Before Writing A Task

### 1. Establish Session Conventions

If this is the first task in the current conversation and the repository does not already show a convention, ask for:

- The last task ID used, or permission to start with `TASK-001`.
- The desired output format: inline markdown, standalone task file, or backlog document.

If the user or repository already provides these conventions, continue with them without asking.

### 2. Evaluate Clarity

Write the task directly when the request has clear scope, expected behavior, and success criteria.

Ask targeted clarifying questions only when missing information would create ambiguity about:

- expected behavior, input, or output
- important edge cases
- dependency on existing components
- priority, status, or sequencing
- whether related work is in or out of scope

Use reasonable defaults for low-risk metadata and state the assumptions. Default status is `Backlog`; default priority is `Medium`.

### 3. Consult Local Project Context When Needed

Check project docs, architecture notes, or existing backlog items when the task:

- affects core abstractions or public APIs
- depends on established conventions
- appears to conflict with existing requirements
- requires sequencing against related work

Raise conflicts before finalizing the task.

## Task Template

Use this structure unless the repository has an established task format:

```markdown
# TASK-XXX: [Concise, Action-Oriented Title]

**Status:** [Backlog | Planned | Pending | In Progress | Done | Cancelled | Duplicate]
**Priority:** [Low | Medium | High | Urgent]
**Dependencies:** [TASK-YYY, TASK-ZZZ | None]
**Complexity:** [Small | Medium | Large]

---

## Description

### Scope

[What this task covers and what it does not cover. Be explicit about boundaries.]

### Acceptance Criteria

1. [Concrete, verifiable condition.]
2. [Concrete, verifiable condition.]
3. [Concrete, verifiable condition.]

### Outcome

[What exists after the task is complete: changed files, new APIs, tests, docs, migration notes, or other deliverables.]

---

## Notes

[Optional context, rationale, references, implementation cautions, or suggested approaches.]
```

## Writing Guidelines

### Title

- Start with a verb such as `Implement`, `Add`, `Refactor`, `Design`, `Extract`, or `Define`.
- Be specific about the deliverable.
- Avoid vague titles such as `Fix things` or `Improve system`.

### Scope

- State what is included.
- State what is excluded.
- If the task is one slice of a larger feature, name the slice.

### Acceptance Criteria

- Each criterion must be testable by unit test, integration test, end-to-end test, or direct inspection.
- Use precise verbs such as `returns`, `throws`, `contains`, `creates`, `rejects`, and `persists`.
- Include important edge cases.
- If a criterion involves a public API, show the expected signature or usage.
- Aim for 4 to 8 criteria. Fewer than 3 often means the task is underspecified; more than 10 often means it should be split.

### Outcome

- List concrete deliverables.
- Mention new files, modified files, public APIs, tests, docs, migrations, or configuration changes when known.
- If the task introduces a public API, include a short signature or usage sketch.

### Notes

- Keep notes useful and concise.
- Include rationale, constraints, references, risks, or recommended approaches.
- Do not hide requirements in notes; requirements belong in acceptance criteria.

### Dependencies And Complexity

- Dependencies reference prerequisite task IDs or `None`.
- Complexity is a rough t-shirt size:
  - `Small`: isolated change, usually one file or a focused fix.
  - `Medium`: touches several files or requires design thought.
  - `Large`: cross-cutting change, new subsystem, migration, or significant coordination.

## Quality Bar

- The task can be understood without reading the conversation history.
- The task has a clear definition of done.
- The task avoids implementation code except for short API sketches.
- The task does not mix unrelated work.
- The task names assumptions explicitly.
