# Contributing

Thank you for contributing to the Enterprise Auth0 Guide. This project follows a task-oriented documentation model similar to Microsoft Learn and AWS documentation.

## Contribution principles

- Write for enterprise identity engineers, platform teams, security teams, and application owners.
- Prefer clear procedures, decision guidance, and reference tables over long narrative.
- Include prerequisites, expected outcomes, validation steps, and rollback guidance when applicable.
- Use Mermaid for architecture and flow diagrams.
- Keep pages vendor-neutral where possible, and call out Auth0-specific configuration explicitly.

## Page structure

Use this structure for implementation and operations pages:

```markdown
# Page title

Brief summary of the task or concept.

## When to use this guidance
## Prerequisites
## Architecture
## Procedure
## Validation
## Troubleshooting
## Next steps
```

## Style guide

- Use sentence case for headings.
- Use active voice.
- Use short paragraphs and scannable lists.
- Use `!!! note`, `!!! tip`, `!!! warning`, and `!!! danger` admonitions for important guidance.
- Use fenced code blocks with language identifiers.

## Local checks

```powershell
mkdocs build --strict
```
