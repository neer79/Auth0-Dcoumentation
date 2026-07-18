# Auth0 CIAM Architecture Blueprint

## Purpose

This document defines a production-oriented Auth0 Customer Identity and Access Management (CIAM) architecture blueprint for a new customer-facing platform. It is intended for developers, architects, product owners, security teams, and implementation stakeholders.

The blueprint covers:

- Business use cases
- Tenant, application, and API structure
- Authentication flows
- Authorization model
- Security controls
- Implementation phases
- Risks and mitigations
- Open questions to finalize the architecture

## Assumptions

This blueprint assumes a modern customer-facing digital platform with:

- Customer web application
- Optional native mobile applications
- Backend APIs and platform services
- Internal admin or support portal
- Possible future B2B or organization-based access
- Potential partner or machine-to-machine API integrations
- Production security, monitoring, and governance requirements

These assumptions should be validated during architecture discovery.

## Executive Summary

Auth0 should be treated as the customer identity control plane, not only as a login provider. The recommended architecture uses Auth0 Universal Login, standards-based OAuth 2.0 and OpenID Connect flows, separate tenants per environment, explicit API authorization, centralized security controls, and operational governance from the start.

High-level login and API access flow:

```text
Customer -> Web/Mobile App -> Auth0 Universal Login -> Identity Source
         -> ID/Access Token -> Backend API -> Authorization Middleware
         -> Platform Services / Data
```

Recommended baseline:

| Area | Recommendation |
|---|---|
| Login UX | Auth0 Universal Login with a branded custom domain |
| Web app | Authorization Code Flow with PKCE, or BFF pattern for higher security |
| Mobile app | Authorization Code Flow with PKCE |
| Backend APIs | Validate JWT access tokens using issuer, audience, signature, expiry, scopes, and organization context |
| Machine clients | Client Credentials Flow with least-privilege client grants |
| Environments | Separate Auth0 tenants for development, staging, and production |
| Authorization | API scopes, permissions, roles, and organization context where needed |
| Extensibility | Auth0 Actions for claims, profile enrichment, MFA decisions, and integration hooks |
| Operations | Log streaming, monitoring, runbooks, and configuration governance |

## Business Use Cases

| Use Case | User Journey | Auth0 Capabilities | Business Outcome |
|---|---|---|---|
| Customer registration | User signs up with email/password, social login, or passwordless | Universal Login, database connection, social connections, email verification | Reduce onboarding friction |
| Customer login | Returning customer authenticates and accesses the platform | OIDC login, sessions, refresh tokens where appropriate | Secure repeat access |
| Profile management | User updates profile, email, phone, or preferences | Management API or app-owned profile service | Improve personalization and support |
| MFA or step-up authentication | Sensitive or risky actions require stronger verification | MFA policies, Actions, risk-based logic | Reduce account takeover risk |
| B2B organization access | User belongs to a company, team, or account | Auth0 Organizations, enterprise connections, organization membership | Support SaaS and delegated access models |
| Partner API access | Partner systems call platform APIs | Machine-to-machine apps, Client Credentials Flow, API scopes | Enable controlled ecosystem access |
| Admin and support access | Internal users support customers or manage operations | Separate admin app, enterprise IdP, MFA, privileged roles | Safer privileged operations |
| Legacy migration | Existing users move into Auth0 | Bulk import, custom database, or progressive migration | Lower migration and rollout risk |
| Audit and compliance | Security and support teams review authentication events | Logs, log streams, attack protection events | Improve visibility and incident response |

## Tenant Model

Use separate Auth0 tenants for each environment:

```text
company-dev.auth0.com
company-staging.auth0.com
company-prod.auth0.com
```

Production should use a branded custom domain:

```text
login.example.com -> Auth0 production tenant
```

Recommended environment boundaries:

| Tenant | Purpose |
|---|---|
| Development | Developer testing, non-production callbacks, sandbox connections |
| Staging | Production-like testing and release validation |
| Production | Real users, hardened settings, restricted administration |

Avoid sharing production connections, clients, secrets, or callback URLs with lower environments.

## Application Structure

| Auth0 Application | Type | Purpose |
|---|---|---|
| `customer-web` | SPA or Regular Web App | Main customer-facing web experience |
| `customer-mobile-ios` | Native | iOS application |
| `customer-mobile-android` | Native | Android application |
| `admin-portal` | Regular Web App | Internal support and administration |
| `partner-dashboard` | Regular Web App or SPA | Optional partner-facing console |
| `backend-bff` | Regular Web App | Backend-for-frontend/session pattern, if used |
| `jobs-worker` | Machine-to-Machine | Internal background jobs |
| `partner-m2m-client-*` | Machine-to-Machine | External partner API clients |

## API / Resource Server Structure

| Auth0 API | Audience | Example Scopes |
|---|---|---|
| `platform-api` | `https://api.example.com` | `read:profile`, `update:profile`, `read:orders`, `create:orders` |
| `admin-api` | `https://admin-api.example.com` | `read:users`, `update:users`, `read:audit` |
| `partner-api` | `https://partner-api.example.com` | `read:catalog`, `create:transaction`, `read:status` |

Keep customer, admin, and partner APIs separate when their risk profiles, audiences, or permission models differ.

## Authentication Flows

### Customer Web Application

Recommended options:

1. Backend-for-frontend or server-side session pattern for higher-security platforms.
2. SPA with Authorization Code Flow with PKCE for simpler client-heavy apps.

For sensitive applications, prefer the BFF pattern so the browser holds only a secure, HTTP-only, same-site session cookie while tokens remain server-side.

SPA flow:

```text
User -> Web App -> Auth0 Universal Login
     -> Email/Social/Enterprise Connection
     -> Authorization Code + PKCE
     -> App receives tokens
     -> API calls with access token
```

BFF flow:

```text
User -> Web App -> Backend/BFF -> Auth0 Universal Login
     -> Authorization Code
     -> Backend stores tokens server-side
     -> Browser receives secure session cookie
     -> Backend calls APIs
```

### Mobile Applications

Use Authorization Code Flow with PKCE through the system browser or platform-recommended browser mechanism. Store refresh tokens only in secure platform storage.

```text
Mobile App -> System Browser -> Auth0
           -> Authorization Code + PKCE
           -> Mobile App receives tokens
           -> API calls with access token
```

### Admin Portal

Use enterprise SSO where possible, strict MFA, shorter sessions, and separate privileged roles.

```text
Admin -> Admin Portal -> Auth0 -> Corporate IdP -> MFA -> Admin API
```

### Machine-to-Machine Access

Use Client Credentials Flow with narrow scopes and explicit client grants.

```text
Worker / Partner System -> Auth0 Token Endpoint
                         -> Access Token with scopes
                         -> API
```

## Authorization Model

Authorization should be layered. Do not rely on frontend route hiding or decoded tokens without validation.

### Layer 1: Token Validation

Every API must validate:

```text
iss: expected issuer
aud: expected API audience
signature: valid against Auth0 JWKS
exp: not expired
scope/permissions: sufficient for operation
organization context: valid where applicable
```

### Layer 2: API Scopes and Permissions

Use scopes for API-level capabilities:

```text
read:profile
update:profile
read:orders
create:orders
read:organization
manage:organization_members
```

### Layer 3: Roles

Use roles to bundle permissions:

| Role | Typical Permissions |
|---|---|
| Customer | `read:profile`, `update:profile`, `read:orders` |
| Organization Admin | `manage:organization_members`, `read:organization` |
| Support Agent | `read:users`, `read:audit` |
| Platform Admin | Privileged admin permissions |
| Partner App | Partner-specific API scopes |

### Layer 4: Organization Context

For B2B or multi-tenant SaaS, use organization context and enforce it server-side:

```text
Token organization ID == requested organization
User has valid membership in organization
User role allows requested action
Resource belongs to organization
```

### Layer 5: Business Policy

Keep complex business decisions in application services or a policy service.

Examples:

- Can this user approve this transaction amount?
- Can this partner access this customer account?
- Can this support agent view personally identifiable information?
- Can this organization admin invite users from this email domain?

## Security Controls

### Identity Security

| Control | Recommendation |
|---|---|
| Universal Login | Prefer hosted login to reduce credential-handling risk |
| MFA | Require for admins, support users, high-risk customers, and sensitive actions |
| Password policy | Enforce strong policy, breached password detection, and email verification |
| Bot protection | Enable after confirming all login flows support it |
| Brute-force protection | Keep enabled and tune thresholds carefully |
| Suspicious IP throttling | Enable where appropriate |
| Custom domain | Use a branded production login domain |
| Social login | Limit providers to approved business providers |
| Enterprise federation | Use SAML or OIDC for B2B customers where required |

### Token Security

Rules:

- Do not accept unsigned or unverified JWTs.
- Do not trust decoded tokens without signature, issuer, audience, expiry, and claim checks.
- Keep access tokens short-lived.
- Use refresh tokens carefully, with rotation where appropriate.
- Do not store secrets in browser or mobile code.
- Do not place sensitive PII, credentials, or secrets in custom claims.
- Validate organization and tenant context in APIs.

### Application Security

- Use HTTPS everywhere.
- Use secure, HTTP-only cookies for BFF/session applications.
- Apply CSRF protection where cookies are used.
- Harden against XSS, especially for SPA token handling.
- Restrict callback and logout URLs per environment.
- Use least-privilege Management API access.
- Separate admin applications from customer applications.

### Operational Security

- Use controlled configuration changes.
- Restrict Auth0 dashboard administrator access.
- Enable log streaming to SIEM or observability tooling.
- Alert on failed login spikes, MFA failures, bot activity, breached password events, suspicious IP activity, admin changes, and Management API activity.
- Maintain incident runbooks for account takeover, credential stuffing, callback URL misconfiguration, key rotation, and tenant outage scenarios.

## Actions and Custom Claims

Use Auth0 Actions deliberately, with versioning, tests, and rollback planning.

Common Actions:

| Trigger | Purpose |
|---|---|
| Post Login | Add custom claims, enforce profile completion, assign default roles, check organization context |
| Post User Registration | Initialize app profile, send welcome event |
| Credentials Exchange | Add claims for machine-to-machine clients |
| Pre User Registration | Validate allowed domains, block disposable emails, apply invitation rules |

Example namespaced custom claims:

```json
{
  "https://example.com/user_id": "app-user-123",
  "https://example.com/org_id": "org_abc",
  "https://example.com/roles": ["org_admin"]
}
```

Keep claims stable, minimal, and non-sensitive.

## Logical Architecture

```text
                         +----------------------+
                         |  Auth0 Production    |
                         |  login.example.com   |
                         +----------+-----------+
                                    |
        +---------------------------+----------------------------+
        |                           |                            |
+-------v--------+        +---------v--------+          +--------v--------+
| Customer Web   |        | Mobile Apps      |          | Admin Portal    |
| SPA or BFF     |        | iOS / Android    |          | Internal Users  |
+-------+--------+        +---------+--------+          +--------+--------+
        |                           |                            |
        +-------------+-------------+----------------------------+
                      |
              +-------v--------+
              | API Gateway /   |
              | Backend APIs    |
              +-------+--------+
                      |
       +--------------+---------------+
       |              |               |
+------v-----+ +------v------+ +------v------+
| User/Profile| | Orders/Core | | Audit/Admin |
| Service     | | Services    | | Services    |
+-------------+ +-------------+ +-------------+
```

## Implementation Phases

### Phase 1: Foundation

- Create development, staging, and production tenants.
- Configure production custom domain.
- Define applications and APIs.
- Configure Universal Login branding.
- Set callback and logout URLs per environment.
- Establish Auth0 administrator access model.
- Document tenant naming, ownership, and promotion process.

### Phase 2: Core Authentication

- Implement customer web login.
- Implement mobile login if required.
- Add email verification and password policy.
- Configure database, social, or enterprise connections.
- Add logout and session handling.
- Add Auth0 SDK integration.

### Phase 3: API Authorization

- Define API audiences and scopes.
- Implement JWT validation middleware.
- Add permission checks to protected endpoints.
- Configure roles and initial permission sets.
- Add machine-to-machine clients for backend jobs.

### Phase 4: B2B / Organization Support

- Introduce Organizations if customer accounts, teams, companies, or B2B tenants are required.
- Model organization roles and membership lifecycle.
- Build invitation and delegated administration flows.
- Add organization-aware authorization in APIs.

### Phase 5: Security Hardening

- Enable MFA policies.
- Enable attack protection features.
- Add step-up authentication for sensitive actions.
- Review token lifetimes and refresh token behavior.
- Lock down Management API access.
- Add security monitoring and alerts.

### Phase 6: Operations and Governance

- Add log streaming.
- Build support and incident runbooks.
- Add dashboards for login health, conversion, failures, MFA friction, and attack signals.
- Manage Auth0 configuration through controlled deployment.
- Define change approval and rollback process.

### Phase 7: Migration and Scale

- Migrate legacy users if applicable.
- Run pilot cohorts.
- Monitor login conversion and authentication errors.
- Tune policies based on production behavior.
- Prepare support training and incident response.

## Risks and Mitigations

| Risk | Impact | Mitigation |
|---|---|---|
| Weak token validation | Unauthorized API access | Enforce issuer, audience, signature, expiry, scopes, and organization checks |
| Overloaded roles | Authorization becomes brittle | Keep roles coarse and enforce business rules in APIs |
| Too much logic in Actions | Identity flows become hard to test and operate | Version Actions, test them, and keep logic minimal |
| SPA token leakage | Account compromise | Prefer BFF for sensitive apps; avoid localStorage; harden XSS controls |
| Misconfigured callback URLs | Redirect or token leakage risk | Use environment-specific allowlists and release review |
| No organization boundary enforcement | Cross-tenant data exposure | Enforce organization/resource ownership server-side |
| MFA friction | Lower conversion or higher support burden | Use step-up or risk-based MFA where appropriate |
| Poor migration planning | User lockouts and support spikes | Pilot migration, rollback plan, and clear user communication |
| Management API overprivilege | Tenant-wide damage | Use least-privilege machine clients and credential rotation |
| Missing monitoring | Slow incident detection | Use log streaming, alerts, and runbooks |

## Architecture Decisions

| Decision | Recommendation | Rationale |
|---|---|---|
| Login surface | Universal Login | Hosted, secure, and easier to maintain |
| Environment model | Separate tenants | Reduces production risk and configuration bleed |
| Customer web pattern | BFF if high security; SPA with PKCE if simpler | Balances security and delivery speed |
| Authorization | Scopes, roles, organization context, and API policy | Avoids frontend-only authorization |
| B2B model | Auth0 Organizations if needed | Provides a clean account and team boundary |
| Custom logic | Actions with governance | Powerful extension point requiring lifecycle discipline |
| API access | Separate resource servers by audience/risk | Clearer permissions and validation |
| Operations | Log streaming and runbooks | Production identity needs active monitoring |

## Open Questions

These questions should be answered before finalizing the production architecture:

1. Is the platform B2C only, B2B only, or mixed B2B2C?
2. Will users belong to companies, households, teams, or only individual accounts?
3. Are mobile apps required at launch?
4. Is the frontend a SPA, server-rendered app, or BFF architecture?
5. Are enterprise customers expected to require SAML or OIDC federation?
6. What compliance constraints apply, such as GDPR, SOC 2, HIPAA, PCI, or data residency?
7. Will legacy users be migrated?
8. Who operates customer support, and what privileges do support agents need?
9. What are the expected scale, geographies, and availability requirements?
10. Which actions require step-up MFA, such as payments, PII changes, admin changes, or exports?
11. What identity providers should be supported at launch?
12. What profile data is mandatory at registration versus collected progressively?
13. What lifecycle events are required for account deletion, deactivation, reactivation, and data export?
14. What downstream systems need identity events?
15. What operational metrics define authentication success?

## Recommended Starting Blueprint

For a new customer-facing platform, start with:

- Separate Auth0 tenants per environment.
- Universal Login on a production custom domain.
- Authorization Code Flow with PKCE.
- BFF pattern if the platform handles sensitive customer data.
- Explicit API scopes and permissions.
- Organization-aware authorization if B2B is likely.
- MFA for administrators and privileged users from day one.
- Attack protection after login-flow testing.
- Log streaming before public launch.
- A documented rollout, rollback, and support plan.

## References

- Auth0 Create Tenants: https://auth0.com/docs/get-started/auth0-overview/create-tenants
- Auth0 Custom Domains: https://auth0.com/docs/customize/custom-domains
- Auth0 Bot Detection: https://auth0.com/docs/secure/attack-protection/bot-detection
- Auth0 Brute-force Protection: https://auth0.com/docs/secure/attack-protection/brute-force-protection
- Auth0 Client Grants: https://auth0.com/docs/get-started/applications/application-access-to-apis-client-grants
