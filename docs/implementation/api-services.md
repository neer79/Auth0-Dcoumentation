# API Services

API services must validate access tokens and enforce authorization for every protected operation.

## Configuration requirements

- API identifier is stable and documented.
- Scopes are reviewed by the API owner.
- Token lifetime is approved.
- Consuming applications are known.
- Monitoring is in place for authorization failures.

## Implementation guidance

- Use maintained JWT middleware.
- Validate issuer, audience, signature, expiration, and required scopes.
- Cache JWKS according to library guidance.
- Return appropriate HTTP status codes.
- Avoid logging full tokens.
- Include correlation IDs in logs where available.

## Response guidance

| Scenario | Typical response |
| --- | --- |
| Missing token | `401 Unauthorized` |
| Invalid token | `401 Unauthorized` |
| Valid token missing scope | `403 Forbidden` |
| Valid token authorized | Proceed with request |

## Production checklist

- [ ] API rejects missing tokens.
- [ ] API rejects wrong audience.
- [ ] API rejects expired tokens.
- [ ] API enforces scopes or permissions.
- [ ] Authorization failures are observable.
