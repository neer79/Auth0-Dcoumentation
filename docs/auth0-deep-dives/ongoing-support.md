# Ongoing Support Model

Ongoing support defines how the enterprise runs Auth0 after initial setup. It covers request intake, application support, customer IdP support, incidents, access reviews, monitoring, and lifecycle maintenance.

## Support tiers

| Tier | Responsibilities |
| --- | --- |
| Tier 1 support | User-facing triage, known issue scripts, basic account recovery routing |
| Application team | Application callback/session/token handling, app-specific authorization, user experience |
| Identity platform team | Tenant configuration, applications, APIs, connections, Actions, organizations |
| Security operations | Attack events, suspicious authentication, MFA incidents, privileged access |
| Vendor support | Auth0 service issues, product defects, support escalations |

## Request types

| Request | Required information |
| --- | --- |
| New application onboarding | Intake form, app type, URLs, owners, scopes, timeline |
| New customer IdP | Customer org, protocol, metadata, attributes, test users |
| MFA reset | User identity, verification evidence, approver, reason |
| Callback change | Application, environment, exact URL, release window |
| Secret rotation | Client, environment, vault record, validation plan |
| Production incident | Tenant, app, connection, time window, user impact |
| Organization change | Customer org, membership or connection change, approver |

## Operating rhythm

- Daily: monitor production alerts and login health.
- Weekly: review pending onboarding and high-risk changes.
- Monthly: review incidents, support trends, and failed login patterns.
- Quarterly: review admin access, privileged roles, unused applications, and customer IdP certificates.
- Semiannually: review architecture decisions, tenant strategy, and security exceptions.

## Support runbooks

Maintain runbooks for:

- Login failure triage.
- Callback mismatch.
- Federation outage.
- MFA reset and recovery.
- Passwordless delivery issue.
- SMS delivery issue.
- Action failure blocking login.
- Signing key or certificate rotation.
- Log stream delivery failure.
- Customer IdP certificate expiry.

## Metrics

Track:

- Login success rate.
- Failed login rate by connection and app.
- MFA challenge and failure rate.
- Password reset and account recovery volume.
- Customer IdP onboarding lead time.
- Application onboarding lead time.
- Production incidents by root cause.
- Configuration drift findings.

## Knowledge management

Support teams need access to:

- Application inventory.
- Customer IdP registry.
- Organization registry.
- Tenant configuration baseline.
- Recent releases.
- Known issues.
- Escalation contacts.
- Auth0 status page and vendor support process.

## Checklist

- [ ] Support ownership is documented.
- [ ] Request intake forms exist.
- [ ] Runbooks cover top failure modes.
- [ ] Monitoring dashboards are available.
- [ ] Access and certificate reviews are scheduled.
- [ ] Vendor escalation path is documented.
