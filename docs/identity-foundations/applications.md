# Applications

Applications represent clients that use Auth0 for authentication. Each application must have an owner, a supported authentication flow, approved redirect settings, and secure credential handling.

## Application types

| Type | Use for | Recommended flow |
| --- | --- | --- |
| Single Page Application | Browser apps without a trusted backend | Authorization Code with PKCE |
| Regular Web Application | Server-rendered apps or backend-for-frontend patterns | Authorization Code |
| Native Application | Mobile or desktop clients | Authorization Code with PKCE |
| Machine to Machine | Service-to-service integrations | Client Credentials |

## Required metadata

- Business owner.
- Technical owner.
- Environment.
- Application type.
- Approved authentication flow.
- Callback URLs.
- Logout URLs.
- Allowed web origins.
- Associated APIs and scopes.
- Secret storage location for confidential clients.

## Callback and logout guidance

- Use exact URLs. Avoid broad or wildcard redirect patterns unless explicitly approved.
- Separate development, staging, and production URLs.
- Remove temporary localhost URLs before production launch unless the client is explicitly for development.
- Review logout behavior with application teams so users do not remain signed in unexpectedly.

## Security requirements

- Public clients must use PKCE.
- Confidential clients must store secrets in an approved secrets manager.
- Client secrets must not be committed to source control.
- Production clients must have an assigned owner and support contact.
- Unused clients must be disabled or deleted through the approved change process.

## Validation checklist

- [ ] Application type matches the workload.
- [ ] Redirect URLs are exact and environment-specific.
- [ ] Logout URLs are approved.
- [ ] Required APIs and scopes are documented.
- [ ] Secret handling is documented for confidential clients.
