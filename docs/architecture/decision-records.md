# Decision records

Architecture decision records document important identity platform decisions, the tradeoffs considered, and the consequences accepted by the team.

## When to create a decision record

Create a record when a decision affects:

- Tenant or environment boundaries.
- Security controls.
- Production release process.
- Federation or provisioning strategy.
- Token, session, or MFA policies.
- Operational ownership or support model.

## Template

```markdown
# ADR-NNN: Title

## Status

Proposed | Accepted | Superseded

## Context

Describe the problem, constraints, and relevant background.

## Options considered

List the realistic options and summarize tradeoffs.

## Decision

State the selected option clearly.

## Consequences

Describe benefits, risks, follow-up work, and operational impact.

## References

Link to related documentation, tickets, or review records.
```

## Initial decision backlog

| ID | Decision | Status | Owner |
| --- | --- | --- | --- |
| ADR-001 | Tenant isolation strategy | Proposed | Identity platform |
| ADR-002 | Custom domain strategy | Proposed | Identity platform |
| ADR-003 | Configuration promotion model | Proposed | Platform automation |
| ADR-004 | MFA enforcement model | Proposed | Security architecture |
| ADR-005 | Log streaming and retention | Proposed | Security operations |

## Review cadence

Review accepted decisions at least twice per year or whenever Auth0 architecture changes materially. Supersede records instead of editing history so future reviewers can understand why the platform evolved.
