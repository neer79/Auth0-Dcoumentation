# OAuth 2.0 and OIDC

OAuth 2.0 is used for delegated authorization. OpenID Connect builds on OAuth 2.0 to provide authentication and identity claims. Enterprise Auth0 implementations should standardize which flows are approved for each workload type.

## Approved flow guidance

| Workload | Recommended flow | Notes |
| --- | --- | --- |
| Single page application | Authorization Code with PKCE | Avoid implicit flow for new apps |
| Native or mobile app | Authorization Code with PKCE | Use system browser patterns |
| Server-side web app | Authorization Code | Use confidential client credentials |
| Service-to-service | Client Credentials | Use least-privilege scopes |
| Limited input device | Device Authorization | Monitor polling and user code abuse |

## Token types

| Token | Purpose | Handling guidance |
| --- | --- | --- |
| ID token | Proves authentication to the client | Do not use as API authorization proof |
| Access token | Authorizes access to APIs | Validate in APIs before accepting |
| Refresh token | Obtains new tokens without user interaction | Rotate and store securely |

## Enterprise requirements

- Use modern flows only for new integrations.
- Validate access tokens in APIs.
- Use PKCE for public clients.
- Restrict scopes to required capabilities.
- Define token lifetimes by workload risk.
- Review refresh token usage and rotation settings.

!!! warning
    The ID token is for the client. APIs should authorize requests using access tokens with the correct audience and scopes.

## Validation checklist

- [ ] Flow is approved for the application type.
- [ ] PKCE is enabled for public clients.
- [ ] API audience is requested where needed.
- [ ] Access token validation is implemented.
- [ ] Refresh token policy is documented.
