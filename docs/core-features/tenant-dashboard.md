# Tenant and Dashboard

An Auth0 tenant is the container for configuration, runtime behavior, and administration. The Auth0 Dashboard is the primary interactive administration interface for tenant resources.

## What the tenant contains

- Applications and client settings.
- APIs and authorization server settings.
- Connections and enterprise identity providers.
- Universal Login, branding, custom domains, and email templates.
- Organizations, invitations, and membership configuration.
- Actions, triggers, secrets, and extensibility configuration.
- Security settings such as MFA, attack protection, sessions, and anomaly detection.
- Logs, log streams, and administrative events.

## Dashboard feature areas

| Dashboard area | Enterprise purpose |
| --- | --- |
| Applications | Configure app clients, callbacks, grant types, credentials, and metadata |
| APIs | Define resource servers, scopes, token settings, and RBAC behavior |
| Authentication | Configure database, social, enterprise, passwordless, and custom connections |
| Organizations | Manage B2B tenants, memberships, branding, and connection routing |
| Actions | Create and bind extensibility logic to Auth0 flows |
| Security | Configure MFA, attack protection, bot detection, and session controls |
| Monitoring | Review logs, streams, and operational events |
| Settings | Configure tenant domains, custom domains, signing keys, and advanced tenant settings |

## Enterprise controls

- Restrict production dashboard access to named administrators.
- Require MFA for all dashboard administrators.
- Use dashboard roles that match job responsibilities.
- Prefer source-controlled automation for repeatable changes.
- Record emergency dashboard changes and reconcile them back into source control.
- Monitor administrator activity and configuration changes.

## Tenant settings to document

- Tenant name and Auth0 domain.
- Environment classification.
- Custom domain and certificate ownership.
- Signing key rotation process.
- Allowed administrator roles.
- Log stream destinations.
- Change management process.

## Validation checklist

- [ ] Tenant owner and backup owner are documented.
- [ ] Administrator MFA is enforced.
- [ ] Dashboard roles are least privilege.
- [ ] Production changes are traceable.
- [ ] Log streams and admin events are monitored.
