---
name: csharp-xml-docs
description: Use when writing, reviewing, or fixing C# XML documentation comments for public C# APIs, including summary, remarks, param, returns, exception, see, and paramref tags.
---

# C# XML Docs

## Purpose

Write C# XML documentation comments that describe the public contract of an API: what it does, when to use it, what values mean, and what callers can rely on.

## When To Use

Use this skill when the user asks to write, add, review, fix, or improve C# XML docs. Also use it when generating public C# types or members in a codebase that expects XML documentation.

Common triggers include:

- "add XML docs"
- "document this"
- "write the docs"
- "review the comments"
- "fix the summary"
- requests involving `<summary>`, `<remarks>`, `<param>`, `<returns>`, or `<exception>`

## Workflow

1. Identify the public API surface that needs documentation.
2. Describe observable behavior and caller-facing contracts, not implementation details.
3. Add required tags for the member kind.
4. Use XML documentation references for types, members, parameters, and language keywords.
5. Review each comment for accuracy, completeness, and valid XML syntax.

## Tag Taxonomy

| Tag | Purpose | Required On |
|---|---|---|
| `<summary>` | One-sentence description of what the member does | Every public member |
| `<remarks>` | Context, constraints, side effects, ordering, or invariants | Complex types and non-obvious members |
| `<param name="...">` | Parameter meaning and constraints | Every public method and constructor parameter |
| `<returns>` | Meaning of the returned value | Non-void public methods and properties where helpful |
| `<exception cref="...">` | Condition that causes an exception | Every explicitly documented or thrown exception |
| `<see cref="...">` | Cross-reference to a type or member | Inline where precision helps |
| `<paramref name="...">` | Inline reference to a parameter | Inside prose that mentions a parameter |
| `<para>` | Paragraph break inside remarks | Multi-paragraph remarks |

## Core Rules

### Summary

- Answer "what does this do?" in one sentence.
- Start method and constructor summaries with active verbs such as `Creates`, `Returns`, `Builds`, or `Validates`.
- Start property summaries with `Gets` or `Gets or sets`.
- Start type summaries with `Represents`, `Defines`, or another precise contract word.
- Do not repeat the member name.
- Do not explain implementation details.
- End with a period.

### Remarks

- Use remarks for architectural context, behavioral contracts, side effects, ordering constraints, and invariants.
- Split distinct ideas with `<para>`.
- Omit remarks for self-evident members.
- Prefer caller-facing language over implementation narrative.

### Parameters

- Explain what the value represents.
- Include important constraints such as nullability, valid ranges, or optional behavior.
- Use `<paramref name="..."/>` when referencing another parameter in prose.

### Returns

- Explain what the returned value represents, not just its type.
- Mention empty results, null behavior, or ownership expectations when relevant.

### Exceptions

- Use one `<exception>` element per exception type.
- State the exact condition that causes the exception.
- Prefer "Thrown when ..." phrasing.

### Cross-References

- Use `<see cref="..."/>` for types and members.
- Use `<paramref name="..."/>` for parameters.
- Use `<see langword="null"/>`, `<see langword="true"/>`, and `<see langword="false"/>` for language keywords.

## Example

```csharp
/// <summary>
/// Returns the normalized representation of the specified value.
/// </summary>
/// <param name="value">The value to normalize.</param>
/// <returns>The normalized representation of <paramref name="value"/>.</returns>
/// <exception cref="ArgumentNullException">
/// Thrown when <paramref name="value"/> is <see langword="null"/>.
/// </exception>
public string Normalize(string value)
{
    ArgumentNullException.ThrowIfNull(value);
    return value.Trim();
}
```

## Review Checklist

- Every public member has a useful `<summary>`.
- Parameters, return values, and exceptions are documented where applicable.
- Comments describe public behavior instead of implementation mechanics.
- XML tags are well-formed and reference existing names.
- The wording adds information that is not already obvious from the member name and signature.
