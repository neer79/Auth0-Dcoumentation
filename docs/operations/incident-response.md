# Incident response

Incident response procedures define how teams investigate, contain, remediate, and learn from identity-related events.

## Common incident types

- Credential compromise.
- Federation outage.
- MFA enrollment or challenge failure.
- Token misuse or suspicious token exchange.
- Misconfigured callback or logout URL.
- Excessive failed logins.
- Action failure blocking authentication.

## Severity considerations

| Signal | Severity factor |
| --- | --- |
| Production authentication outage | High availability impact |
| Privileged account compromise | High security impact |
| Single application callback error | Scope depends on affected users |
| Log stream outage | Monitoring and evidence risk |

## Response workflow

1. Triage severity and affected population.
2. Preserve Auth0, application, and identity provider logs.
3. Identify recent changes.
4. Contain affected users, applications, or connections.
5. Apply remediation or rollback.
6. Validate recovery.
7. Communicate status.
8. Document timeline, root cause, and follow-up actions.

## Evidence to collect

- Auth0 event IDs and timestamps.
- Affected tenant, application, connection, and organization.
- Recent release or configuration changes.
- Screenshots or exports of relevant settings.
- Remediation actions and owners.

## Post-incident review

- What detection worked?
- What detection was missing?
- Did the runbook work?
- Was rollback clear?
- What documentation needs updating?
