# Logs, Events, and Monitoring

Auth0 logs and events provide the evidence needed to troubleshoot authentication issues, monitor security signals, and support audits. Production tenants should stream logs to enterprise monitoring systems.

## Event categories

| Category | Examples |
| --- | --- |
| Authentication | Successful login, failed login, logout, password reset |
| Federation | Enterprise connection success or failure, SAML/OIDC errors |
| MFA | Enrollment, challenge, success, failure |
| Token | Token exchange success or failure, client credentials activity |
| Security | Attack protection, breached password, suspicious activity |
| Administration | Dashboard or Management API configuration changes |
| Extensibility | Action execution success or failure |

## Log streams

Use log streams to export Auth0 events to systems such as SIEM, log analytics, event streaming, or custom webhook destinations. Production log streaming should be treated as a required operational control.

## Monitoring dashboards

Dashboards should include:

- Login volume and success rate.
- Failure rate by application and connection.
- Federation error trends.
- MFA enrollment and challenge failures.
- Attack protection events.
- Management API activity.
- Action execution errors.
- Log stream delivery health.

## Investigation fields

When investigating an event, capture:

- Tenant and environment.
- Application or client ID.
- Connection or organization.
- User identifier, if policy allows.
- Event type and timestamp.
- IP address and user agent, where relevant.
- Correlation ID or request ID if available.

## Validation checklist

- [ ] Production logs are streamed to enterprise monitoring.
- [ ] Log access is restricted.
- [ ] Alert owners are assigned.
- [ ] Event retention meets policy.
- [ ] Incident runbooks reference relevant event types.
