# Operations model

The operations model defines who runs Auth0, how production changes occur, how incidents are handled, and how evidence is captured.

## Responsibility matrix

| Area | Primary owner | Supporting teams |
| --- | --- | --- |
| Tenant administration | Identity platform team | Security architecture |
| Application integration | Application teams | Identity platform team |
| Security monitoring | Security operations | Identity platform team |
| Release management | Platform automation | Application teams |
| Incident response | Identity and SRE teams | Security operations |
| Compliance evidence | Governance team | Identity platform team |

## Operating ceremonies

- Weekly review of upcoming identity configuration changes.
- Monthly review of incidents, alerts, and operational metrics.
- Quarterly access review for tenant administrators and privileged roles.
- Quarterly review of application inventory and unused clients.
- Semiannual review of architecture decisions and security exceptions.

## Standard operational records

- Tenant inventory.
- Application inventory.
- API and scope catalog.
- Identity provider registry.
- Release history.
- Incident records.
- Access review evidence.
- Security exception register.

## Service health signals

- Authentication success rate.
- Login error rate by connection.
- Token exchange failures.
- MFA failure and enrollment rates.
- Action execution errors.
- Log stream delivery status.
