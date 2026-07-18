# Log Event Taxonomy

Auth0 emits event logs for authentication, administration, security, user lifecycle, token, and extensibility activity. A useful enterprise monitoring strategy groups these events by operational meaning, not only by raw event code.

## Monitoring categories

| Category | Event examples to monitor | Operational use |
| --- | --- | --- |
| Successful authentication | Login success, SSO success | Baseline volume and user activity |
| Failed authentication | Invalid credentials, blocked user, failed federation | Troubleshooting and attack detection |
| MFA | Enrollment, challenge, failure, recovery | Assurance and support monitoring |
| Token exchange | Authorization code exchange, refresh, client credentials | API and service identity troubleshooting |
| Federation | SAML/OIDC errors, provider failures | Enterprise IdP support and outage detection |
| User lifecycle | Signup, password reset, email verification, block/unblock | Support and audit evidence |
| Administration | Dashboard and Management API configuration changes | Change control and privileged activity monitoring |
| Security | Attack protection, breached password, suspicious activity | Incident detection and response |
| Extensibility | Action success, error, timeout | Custom flow reliability |

## Alerting priorities

High-priority alerts should usually include:

- Production login failure spike.
- Federation connection outage.
- Administrator account failure or suspicious login.
- MFA failure spike after policy change.
- Log stream delivery failure.
- Management API write activity outside deployment windows.
- Action errors in login-critical flows.

## Event enrichment

Where possible, enrich events with:

- Tenant and environment.
- Application owner.
- Connection owner.
- Organization or customer identifier.
- Release version or deployment window.
- Severity mapping.

## Retention and privacy

Auth0 logs can contain user identifiers, IP addresses, user agents, and operational metadata. Apply retention, access control, and privacy handling according to policy.

## Validation checklist

- [ ] Event categories are mapped to monitoring rules.
- [ ] Alerts have owners and runbooks.
- [ ] Production log retention meets policy.
- [ ] Management API writes are monitored.
- [ ] Log event handling respects privacy requirements.
