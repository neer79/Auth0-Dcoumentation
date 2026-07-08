# Enterprise federation overview

Enterprise federation connects Auth0 to external identity providers so applications can rely on Auth0 while users authenticate through their organization identity system.

## Federation objectives

- Delegate authentication to enterprise identity providers.
- Preserve consistent application integration through Auth0.
- Normalize identity claims and user profile data.
- Support organization-specific identity provider routing.
- Enable lifecycle automation through provisioning where required.

## Federation protocols

| Protocol | Use when | Notes |
| --- | --- | --- |
| OIDC | Modern identity provider integration | Preferred when supported by the provider and application requirements |
| SAML | Enterprise and legacy federation | Requires certificate and metadata lifecycle management |
| WS-Fed | Legacy Microsoft federation scenarios | Use only when required by legacy constraints |
| SCIM | User and group provisioning | Complements authentication federation but does not replace it |

## Design decisions

- Which identity provider is authoritative for authentication?
- Which attributes are required by applications?
- How are groups, roles, or entitlements mapped?
- Is just-in-time user creation allowed?
- Are users provisioned before first login?
- How are disabled users removed or blocked?

## Operational requirements

- Track provider metadata and certificate expiration.
- Monitor federation login failures separately from database login failures.
- Document escalation contacts for each provider.
- Test federation after provider-side changes.
- Maintain break glass access for tenant administration.

## Validation checklist

- [ ] Provider owner is documented.
- [ ] Protocol and metadata source are documented.
- [ ] Claims and attribute mappings are reviewed.
- [ ] Login and logout behavior is tested.
- [ ] Failure events are visible in monitoring.
