# AI Context

Centralized, project-agnostic rules and skills for AI agents. Each item is packaged as a self-contained folder with human-facing usage notes and the agent-facing rule or skill file.

## Skills

| Skill | Agent file | What it does |
|---|---|---|
| [C# XML Docs](skills/documentation/csharp-xml-docs/README.md) | [SKILL.md](skills/documentation/csharp-xml-docs/SKILL.md) | Guides agents to write and review C# XML documentation comments for public APIs. |
| [Task Writing](skills/planning/task-writing/README.md) | [SKILL.md](skills/planning/task-writing/SKILL.md) | Turns feature or change requests into precise, implementation-ready development tasks. |
| [Testing Principles](skills/testing/testing-principles/README.md) | [SKILL.md](skills/testing/testing-principles/SKILL.md) | Guides agents to write, review, and structure reliable unit, integration, and end-to-end tests. |

## Rules

| Rule | Rule file | What it does |
|---|---|---|
| [Architecture Decision Records](rules/architecture/architecture-decision-records/README.md) | [RULE.md](rules/architecture/architecture-decision-records/RULE.md) | Requires significant architectural decisions to be captured as concise ADR documents. |

## Repository Layout

```text
skills/
  <domain>/<skill-name>/
    README.md
    SKILL.md
rules/
  <domain>/<rule-name>/
    README.md
    RULE.md
```

Use the `README.md` in each item to understand when and how to apply it. Use `SKILL.md` or `RULE.md` as the copyable agent-facing instruction file.
