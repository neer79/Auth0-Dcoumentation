# Automation overview

Automation reduces configuration drift, improves repeatability, and makes Auth0 changes reviewable. Treat Auth0 configuration as identity infrastructure that moves through the same discipline as application and cloud infrastructure changes.

## Automation scope

| Resource | Automation target |
| --- | --- |
| Tenant settings | Baseline configuration and security settings |
| Applications | Client type, callbacks, logout URLs, origins, grant types |
| APIs | Audiences, scopes, token settings |
| Connections | Provider configuration, enabled clients, metadata references |
| Actions | Code, secrets references, trigger bindings |
| Log streams | Destination and delivery configuration |
| Organizations | Creation, metadata, connection assignment where appropriate |

## Automation principles

- Use source control as the expected configuration state.
- Parameterize environment-specific values.
- Keep secrets in a secrets manager, not in repository files.
- Validate changes before applying them.
- Record who approved production changes.
- Reconcile emergency dashboard changes back into code.

## Tooling options

| Tool | Use for |
| --- | --- |
| Terraform | Declarative configuration and drift management |
| Management API | Custom inventory, validation, migration, and reporting tasks |
| CI/CD | Review, validation, promotion, and evidence capture |
| Policy checks | Enforce baseline requirements before release |

## Maturity path

1. Document manual configuration standards.
2. Automate inventory export and validation.
3. Move stable resources to source-controlled configuration.
4. Add pull request validation and production approvals.
5. Add drift detection and automated compliance evidence.
