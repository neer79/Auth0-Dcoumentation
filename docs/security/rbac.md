# RBAC

Role-based access control maps users, groups, applications, and service identities to authorized capabilities. Auth0 can issue permissions in tokens, but APIs remain responsible for enforcement.

## RBAC design principles

- Model roles around job responsibilities or product capabilities.
- Keep scopes and permissions understandable to API owners.
- Avoid assigning broad administrative access by default.
- Review privileged roles regularly.
- Keep authorization decisions server-side for protected resources.

## Role design example

| Role | Permissions |
| --- | --- |
| Order reader | `orders:read` |
| Order operator | `orders:read`, `orders:write` |
| Order administrator | `orders:read`, `orders:write`, `orders:delete` |

## Enterprise questions

- Are roles assigned in Auth0, the application, or an external system?
- Are group claims mapped from an enterprise identity provider?
- Are roles global or organization-specific?
- How are privileged role assignments approved?
- How are role changes audited?

## Validation checklist

- [ ] Roles map to documented permissions.
- [ ] APIs enforce permissions server-side.
- [ ] Privileged roles require approval.
- [ ] Role assignments are reviewable.
- [ ] Organization-specific authorization is tested where applicable.
