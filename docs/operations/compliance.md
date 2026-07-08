# Compliance

Compliance guidance maps Auth0 controls to evidence, review activities, and accountable owners. The goal is to make control effectiveness reviewable without slowing normal delivery.

## Control areas

| Area | Evidence examples |
| --- | --- |
| Access management | Administrator role review, privileged access approvals |
| Authentication | MFA policy, login logs, session settings |
| Authorization | API scopes, role assignments, access review records |
| Change management | Pull requests, release records, approvals |
| Monitoring | Alert configuration, incident records, log stream status |
| Secrets | Secret rotation records and vault access controls |

## Evidence principles

- Evidence must identify the tenant, environment, date, and owner.
- Evidence should come from source-controlled configuration or system exports where possible.
- Manual screenshots should be temporary and replaced by automated evidence when feasible.
- Exceptions need owners and expiration dates.

## Review cadence

- Administrator access: quarterly.
- Application inventory: quarterly.
- Security baseline: annually or after major architecture change.
- Production changes: every release.
- Incidents: after every incident.

## Validation checklist

- [ ] Evidence owners are assigned.
- [ ] Evidence location is documented.
- [ ] Reviews have a defined cadence.
- [ ] Exceptions are tracked.
- [ ] Compliance requirements are mapped to platform controls.
