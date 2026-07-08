# Token best practices

Tokens must be scoped, validated, and handled according to enterprise security requirements. Token settings should be reviewed for every application and API before production launch.

## Token handling rules

- Use access tokens for API authorization.
- Use ID tokens only for client authentication context.
- Keep access tokens short-lived.
- Use refresh token rotation where refresh tokens are required.
- Do not store tokens in insecure browser storage.
- Do not place sensitive data in tokens unless required and approved.

## Claims guidance

- Include only claims required by clients or APIs.
- Prefer stable identifiers for subject correlation.
- Avoid embedding large group lists when authorization can be resolved another way.
- Use custom claims namespaces consistently.

## Lifetime considerations

| Token | Guidance |
| --- | --- |
| Access token | Short lifetime based on application risk and user experience |
| ID token | Short enough to reflect authentication state appropriately |
| Refresh token | Rotate and revoke on suspicious use |

## Validation checklist

- [ ] Token audiences are documented.
- [ ] Token lifetimes are reviewed.
- [ ] Refresh token rotation is configured where used.
- [ ] APIs validate tokens server-side.
- [ ] Sensitive data is not exposed in claims.
