# Authorization and RBAC

Auth0 authorization capabilities help issue permissions in tokens and model API access. Applications and APIs still need to enforce authorization decisions at runtime.

## Auth0 authorization building blocks

| Building block | Purpose |
| --- | --- |
| API | Defines a protected resource and access token audience |
| Scope | Defines a permission-like capability for an API |
| Permission | RBAC permission associated with an API |
| Role | Collection of permissions assigned to users |
| Organization membership | Context for B2B or tenant-aware access |
| Custom claims | Token claims added through Actions for application-specific needs |

## RBAC modes

Auth0 can support role and permission assignment so access tokens can include permissions for APIs. This is useful when APIs need a centralized permission vocabulary.

## Enterprise design rules

- Model API scopes as stable business capabilities.
- Keep roles understandable and reviewable.
- Avoid putting large or volatile authorization data in tokens.
- Use organization context for B2B access decisions.
- Enforce authorization in APIs and backend services.
- Review privileged role assignments regularly.

## Common authorization patterns

| Pattern | Description |
| --- | --- |
| Scope-based API authorization | API checks for required scopes or permissions |
| Role-based access | User roles map to sets of permissions |
| Organization-aware authorization | Access depends on organization membership and role |
| Application-side entitlements | Application evaluates detailed entitlements from its own data store |

## Validation checklist

- [ ] API scopes and permissions are documented.
- [ ] Role ownership and approval process are defined.
- [ ] APIs enforce permissions server-side.
- [ ] Privileged roles are reviewed periodically.
- [ ] Organization context is validated for B2B workloads.
