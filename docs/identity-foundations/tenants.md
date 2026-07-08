# Tenants

Auth0 tenants are the primary administrative and runtime boundary for identity configuration. Tenant design affects security, release management, federation, logging, and incident response.

## Tenant responsibilities

A tenant contains configuration for:

- Applications and APIs.
- Connections and identity providers.
- Organizations and membership settings.
- Actions and extensibility code.
- Branding, Universal Login, and custom domains.
- Log streams, anomaly detection, and tenant-level security settings.

## Enterprise configuration baseline

| Area | Required baseline |
| --- | --- |
| Ownership | Assign primary and backup tenant owners |
| Administration | Require MFA for dashboard administrators |
| Access | Use least-privilege dashboard roles |
| Logging | Stream production logs to a monitored destination |
| Domains | Use custom domains for production user-facing applications |
| Automation | Manage repeatable configuration through source control |

## Tenant metadata

Track tenant metadata in the platform inventory:

- Tenant name and Auth0 domain.
- Environment and business purpose.
- Production or non-production classification.
- Primary owner and escalation contact.
- Custom domain and certificate owner.
- Log stream destination.
- Automation service account owner.

## Operational controls

- Review administrator access at least quarterly.
- Monitor failed administrator logins and dashboard changes.
- Confirm log stream delivery after every release that changes log configuration.
- Keep emergency access accounts documented and monitored.
- Reconcile dashboard changes back into source-controlled configuration.

## Validation checklist

- [ ] Tenant owner and backup owner are documented.
- [ ] Administrator MFA is enforced.
- [ ] Production log streams are enabled.
- [ ] Custom domain is configured where required.
- [ ] Tenant appears in the configuration inventory.
