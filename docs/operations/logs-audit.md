# Logs and audit

Auth0 logs support troubleshooting, security monitoring, incident response, and compliance evidence. Production logs must be streamed to a monitored destination.

## Log uses

| Use case | Examples |
| --- | --- |
| Troubleshooting | Callback errors, federation failures, MFA failures |
| Security monitoring | Attack protection, suspicious logins, administrator events |
| Audit evidence | Access review, configuration change support, incident records |
| Operations | Release validation, service health, integration support |

## Log handling requirements

- Stream logs to enterprise monitoring.
- Define retention and access controls.
- Protect logs that contain personal data.
- Avoid copying sensitive log excerpts into tickets unless necessary.
- Correlate logs with application and infrastructure events.

## Audit evidence examples

- Administrator access review exports.
- Log stream configuration screenshots or configuration state.
- MFA policy configuration.
- Application and API inventory.
- Incident timeline and remediation notes.

## Validation checklist

- [ ] Log stream is enabled for production tenants.
- [ ] Logs are searchable by tenant, application, and connection.
- [ ] Retention meets compliance requirements.
- [ ] Access to logs is restricted.
- [ ] Audit evidence location is documented.
