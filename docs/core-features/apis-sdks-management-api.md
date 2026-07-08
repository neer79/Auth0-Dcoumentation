# APIs, SDKs, and Management API

Auth0 provides APIs and SDKs for application integration, token validation, and administrative automation. Enterprise teams should standardize supported SDKs and control Management API usage carefully.

## Integration surfaces

| Surface | Purpose |
| --- | --- |
| Authentication API | Supports login, token, logout, passwordless, and related runtime operations |
| Management API | Supports administrative configuration and user management automation |
| SDKs | Provide supported integration patterns for common application platforms |
| JWKS endpoint | Provides signing keys for token validation |
| Well-known configuration | Provides OIDC discovery metadata |

## SDK standardization

Application teams should prefer maintained Auth0 SDKs or mature framework-native OIDC libraries. Standardization reduces custom protocol bugs and makes support easier.

Document approved SDKs for:

- JavaScript single page applications.
- Node.js or server-side web applications.
- .NET applications and APIs.
- Java applications and APIs.
- Python applications and APIs.
- iOS and Android mobile apps.

## Management API controls

The Management API can change tenant configuration and user data, so credentials must be protected.

- Use Machine to Machine credentials with least-privilege scopes.
- Use separate credentials per environment.
- Store credentials in a secrets manager.
- Prefer read-only scopes for reporting jobs.
- Require review for scripts that update or delete resources.
- Monitor Management API activity.

## Automation use cases

- Export tenant inventory.
- Validate applications, APIs, connections, and Actions.
- Generate compliance evidence.
- Promote configuration through CI/CD.
- Reconcile drift.
- Support migrations and cleanup.

## Validation checklist

- [ ] Approved SDKs are documented.
- [ ] APIs validate tokens using trusted metadata and keys.
- [ ] Management API credentials are least privilege.
- [ ] Automation credentials are stored securely.
- [ ] Management API activity is monitored.
