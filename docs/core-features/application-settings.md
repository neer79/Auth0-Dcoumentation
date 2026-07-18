# Application Settings

Auth0 Applications define how workloads authenticate users or services. This page documents the Auth0-specific settings that application teams and platform owners must understand before production onboarding.

## Application types

| Auth0 application type | Use for | Security posture |
| --- | --- | --- |
| Single Page Application | Browser-only apps such as React, Angular, or Vue | Public client; must use PKCE; no client secret |
| Regular Web Application | Server-side web apps and backend-for-frontend patterns | Confidential client; protect client secret |
| Native Application | Mobile, desktop, and CLI apps | Public client; use PKCE and platform secure storage |
| Machine to Machine Application | Service-to-service access | Confidential service identity; use client credentials |

## Core settings

| Setting | Meaning | Enterprise guidance |
| --- | --- | --- |
| Name | Display name in the tenant | Include app, environment, and owning team where useful |
| Domain | Tenant or custom domain used by the app | Prefer production custom domain for user-facing apps |
| Client ID | Public identifier for the application | Safe to reference in app config but still inventory it |
| Client Secret | Confidential credential for trusted clients | Store only in a secrets manager |
| Application Type | Determines allowed integration behavior | Match the actual workload type |
| Token Endpoint Authentication Method | How confidential clients authenticate to token endpoint | Use secure methods supported by the app platform |

## URI settings

| URI setting | Purpose | Common mistake |
| --- | --- | --- |
| Allowed Callback URLs | Where Auth0 can redirect after login | Missing exact path or environment hostname |
| Allowed Logout URLs | Where Auth0 can redirect after logout | Assuming app logout also ends IdP session |
| Allowed Web Origins | Browser origins allowed for selected flows | Including paths instead of origins |
| Allowed Origins (CORS) | Origins allowed for cross-origin requests | Overly broad wildcard origins |

## Grant types

Grant types define which OAuth/OIDC flows the application can use. Disable unused grant types where possible.

| Grant type | Typical use |
| --- | --- |
| Authorization Code | Server-side web applications |
| Authorization Code with PKCE | SPAs, native apps, and mobile apps |
| Client Credentials | Machine to Machine applications |
| Refresh Token | Long-lived sessions where policy allows |
| Device Code | Limited input devices and CLIs |

## Add-ons and advanced settings

Some tenants use add-ons or advanced application settings for SAML, WS-Fed, or legacy integration needs. Document these separately because they can change token shape, assertion behavior, or protocol-level outputs.

## Production readiness checklist

- [ ] Application type matches the workload.
- [ ] Callback URLs are exact and environment-specific.
- [ ] Logout URLs are approved.
- [ ] Web origins and CORS origins are minimal.
- [ ] Unused grant types are disabled.
- [ ] Client secret storage is documented.
- [ ] Application owner and support contact are recorded.
