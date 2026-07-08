# Terraform

Terraform can manage Auth0 configuration as code. It is most effective when combined with a clear environment strategy, secrets management, and review process.

## Recommended use cases

- Applications and APIs.
- Scopes and resource servers.
- Connections and enabled clients.
- Actions and trigger bindings.
- Log streams and tenant settings where supported.

## State strategy

Use separate state per environment. Production state should have stricter access controls and change approval requirements than non-production.

| Environment | State guidance |
| --- | --- |
| Development | Team-accessible, lower risk |
| Staging | Controlled, production-like validation |
| Production | Restricted, backed up, access reviewed |

## Module design

- Create reusable modules for standard application patterns.
- Parameterize URLs, domains, and environment-specific names.
- Keep sensitive values out of variables files committed to source control.
- Add outputs that help application teams discover required values.

## Import strategy

For existing tenants:

1. Export or inventory current configuration.
2. Decide which resources Terraform will own.
3. Import resources into state.
4. Run a plan and review differences.
5. Resolve drift before applying changes.

## Validation checklist

- [ ] State storage is secured.
- [ ] Provider credentials are stored in a secret manager.
- [ ] Existing resources are imported before enforcement.
- [ ] Plans are reviewed before production apply.
- [ ] Emergency changes are reconciled back into Terraform.
