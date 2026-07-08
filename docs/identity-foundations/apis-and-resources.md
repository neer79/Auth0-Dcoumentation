# APIs and resources

Auth0 APIs define protected resources and token audiences. API design controls what access tokens are issued for and how services enforce authorization.

## API design principles

- Use stable, unique API identifiers as audiences.
- Model scopes as business capabilities, not UI actions.
- Keep scope names consistent across environments.
- Avoid overly broad scopes such as `admin` unless the privilege is carefully constrained.
- Validate tokens in every API, even when traffic comes from trusted networks.

## Scope design

| Scope pattern | Example | Guidance |
| --- | --- | --- |
| Read access | `orders:read` | Use for list and detail retrieval |
| Write access | `orders:write` | Use for create and update operations |
| Delete access | `orders:delete` | Separate from write when destructive |
| Administrative access | `orders:admin` | Require additional review and monitoring |

## API metadata

Track these fields for each API:

- API name and identifier.
- Owning team.
- Environment.
- Token signing algorithm.
- Token lifetime.
- Scopes and descriptions.
- Consuming applications.
- Monitoring and alerting owner.

## Validation requirements

Every API must validate:

- Token signature.
- Issuer.
- Audience.
- Expiration.
- Required scopes or permissions.

## Review checklist

- [ ] Audience is stable and documented.
- [ ] Scope names are reviewed by the API owner.
- [ ] Token lifetime is approved.
- [ ] API validation is implemented with a maintained library.
- [ ] Privileged scopes have review and monitoring requirements.
