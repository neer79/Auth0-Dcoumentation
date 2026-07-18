# Business Use Cases

Auth0 can support many identity scenarios, but each business use case needs different tenant, connection, authorization, MFA, and operations decisions.

## Use case matrix

| Use case | Typical users | Auth0 capabilities | Key decisions |
| --- | --- | --- | --- |
| Workforce SSO | Employees and contractors | Enterprise connections, Universal Login, SSO, MFA, RBAC | IdP ownership, group/role mapping, session policy |
| Customer identity | Consumers or digital customers | Database connections, passkeys, passwordless, social login, MFA, email templates | Signup, account recovery, fraud controls, branding |
| Partner portal | Partner users outside the company | Organizations, enterprise connections, invitations, MFA, RBAC | Organization lifecycle, delegated administration, IdP onboarding |
| B2B SaaS | Customer tenant users | Organizations, customer IdPs, custom claims, tenant-aware APIs | Tenant isolation, org routing, customer admin model |
| API platform | Internal or external developers | APIs/resource servers, scopes, client credentials, Management API | Audience design, scope governance, service identity lifecycle |
| Machine identity | Backend services and automation | Machine to Machine apps, client credentials, Management API scopes | Secret storage, scope minimization, rotation, monitoring |
| Migration from legacy IAM | Existing app and user estate | Database migration, federation, SAML/OIDC, Actions | Migration waves, coexistence, rollback, user communication |

## Workforce SSO pattern

Workforce SSO usually delegates authentication to an enterprise identity provider such as Microsoft Entra ID, Okta, ADFS, or Google Workspace. Auth0 gives applications one consistent OIDC/OAuth or SAML integration even when upstream identity providers vary.

Key design points:

- Decide whether Auth0 or the upstream IdP controls MFA.
- Decide whether groups are passed in tokens or translated to application roles.
- Align Auth0 session lifetime with workforce security policy.
- Monitor federation failures as enterprise availability events.

## Customer identity pattern

Customer identity usually needs a balance of conversion, security, recovery, and brand experience.

Recommended Auth0 capabilities:

- Universal Login with custom domain and branding.
- Database connection, passkeys, social login, or passwordless depending on product risk.
- Breached password and attack protection controls.
- Email templates for verification, password reset, and account lifecycle.
- Event monitoring for signup, login, password reset, and suspicious activity.

## Partner and B2B SaaS pattern

Partner and B2B SaaS scenarios usually require Organizations and customer-specific IdP onboarding.

Recommended Auth0 capabilities:

- Organization per customer, partner, or account.
- Organization-specific enterprise connections.
- Invitations or SCIM provisioning for membership lifecycle.
- Organization-aware custom claims for APIs.
- Customer IdP onboarding runbook.

## Machine identity pattern

Machine identity should use Machine to Machine applications and client credentials. Do not use shared human accounts or password-based flows for service access.

Controls:

- Dedicated client per service or automation purpose.
- Least-privilege API scopes.
- Secrets in a vault.
- Token exchange monitoring.
- Rotation and decommission procedures.

## Business readiness checklist

- [ ] User population is defined.
- [ ] Primary Auth0 capabilities are selected.
- [ ] Tenant, organization, and connection model is documented.
- [ ] MFA and session policy are approved.
- [ ] Monitoring and support ownership are assigned.
- [ ] Onboarding and offboarding lifecycle is defined.
