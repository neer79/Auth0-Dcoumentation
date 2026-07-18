# APIs and Resource Servers

In Auth0, an API represents a protected resource server. It defines the audience value that clients request and APIs validate in access tokens.

## Core API fields

| Field | Meaning | Enterprise guidance |
| --- | --- | --- |
| Name | Human-readable API name | Use a stable service or product name |
| Identifier | Audience value in access tokens | Treat as a permanent API contract |
| Signing Algorithm | Algorithm used for issued tokens | Prefer asymmetric signing where supported by architecture |
| Token Lifetime | Access token validity period | Keep short and risk-based |
| RBAC Settings | Whether permissions are enforced and included | Use intentionally; avoid token bloat |

## Audience design

The API identifier appears as the `aud` claim in access tokens. APIs must reject tokens with unexpected audiences.

Example audience patterns:

```text
https://api.example.com/orders
urn:example:api:orders
```

Choose one naming convention and keep it stable across application integrations.

## Scope and permission model

| Scope | Description |
| --- | --- |
| `orders:read` | Read order resources |
| `orders:write` | Create or update order resources |
| `orders:delete` | Delete order resources |
| `orders:admin` | Perform privileged order administration |

Scopes should describe API capabilities, not frontend screens.

## Token validation requirements

APIs must validate:

- Issuer.
- Audience.
- Signature.
- Expiration.
- Required scopes or permissions.
- Algorithm expectations.

## Common mistakes

- Using ID tokens to call APIs.
- Accepting any token from the tenant regardless of audience.
- Creating environment-specific scope names.
- Embedding sensitive data or large entitlement lists in access tokens.
- Failing to document which applications consume the API.

## Production checklist

- [ ] API identifier is stable and documented.
- [ ] Scopes are reviewed by API owner.
- [ ] Token lifetime is approved.
- [ ] Consuming applications are inventoried.
- [ ] API validation is implemented and tested.
