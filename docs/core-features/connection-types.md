# Connection Types

Connections determine how users authenticate and where their identities come from. Auth0 supports database, enterprise, social, passwordless, and custom connection patterns.

## Connection categories

| Connection category | Examples | Use for |
| --- | --- | --- |
| Database | Auth0-hosted username/password store | Customer or fallback accounts |
| Enterprise OIDC | Entra ID, Okta, other OIDC providers | Modern workforce or partner federation |
| Enterprise SAML | ADFS, enterprise SAML IdPs | Enterprise federation and legacy providers |
| Social | Google, Apple, GitHub, Facebook | Consumer or developer populations |
| Passwordless | Email link/code, SMS code | Low-friction authentication scenarios |
| Custom database | Legacy user store integration | Migration or gradual modernization |

## Database connection settings

Document these settings for each database connection:

- Password policy.
- Signup behavior.
- Username or email identifier policy.
- Password reset behavior.
- Breached password protection expectations.
- MFA requirements.
- User import or migration strategy.

## Enterprise connection settings

Document these settings for each enterprise connection:

- Protocol: OIDC, SAML, WS-Fed, or other supported protocol.
- Metadata source and owner.
- Client credentials or signing certificate lifecycle.
- Attribute and claims mappings.
- Enabled applications and organizations.
- Provider-side assignment requirements.

## Passwordless settings

Passwordless authentication requires abuse controls:

- Code or link lifetime.
- Retry behavior.
- Rate limiting and monitoring.
- Email or SMS sender governance.
- Recovery and support process.

## Connection assignment

Connections should be enabled only for applications and organizations that need them. Broad connection assignment can cause accidental login paths, confusing user experience, and authorization gaps.

## Validation checklist

- [ ] Connection type and owner are documented.
- [ ] Enabled applications are reviewed.
- [ ] Attribute mappings are documented.
- [ ] Credential or certificate lifecycle is tracked.
- [ ] Failure events are monitored.
