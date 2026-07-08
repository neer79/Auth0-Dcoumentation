# Tenant strategy

Tenant strategy defines how Auth0 tenants map to environments, business units, regions, regulatory boundaries, and user populations.

## Decision criteria

Evaluate tenant boundaries using these criteria:

| Criterion | Consideration |
| --- | --- |
| Environment isolation | Development, staging, and production should not share runtime configuration |
| Regulatory boundary | Some workloads require separate administration or data handling |
| Business ownership | Separate business units may require independent control and release cadence |
| User population | Workforce, customer, partner, and machine identities may need distinct governance |
| Operational complexity | More tenants increase configuration promotion and monitoring overhead |

## Recommended baseline

Use at least one tenant per environment:

- Development tenant for experimentation and integration development.
- Staging tenant for production-like validation.
- Production tenant for live traffic.

Add additional production tenants only when isolation requirements justify the overhead.

## Common models

| Model | Use when | Tradeoff |
| --- | --- | --- |
| Tenant per environment | Most enterprise platforms | Requires configuration promotion controls |
| Tenant per business unit | Business units require independent administration | Increases governance coordination |
| Tenant per region | Data residency or regional operations require separation | Requires regional monitoring and release patterns |
| Tenant per product line | Products have distinct identity populations and risk profiles | Can duplicate shared integrations |

## Naming standard

Use names that identify organization, platform, environment, and purpose. Example pattern:

```text
<company>-<identity-platform>-<environment>
```

Examples:

- `contoso-auth-dev`
- `contoso-auth-stage`
- `contoso-auth-prod`

## Governance requirements

- Assign tenant owners and backup owners.
- Restrict production administrator access.
- Document custom domains and certificate ownership.
- Stream logs from every production tenant.
- Keep tenant metadata in the configuration inventory.

!!! warning
    Avoid using a single production tenant for unrelated identity populations without a documented isolation, authorization, and operations model.

## Validation checklist

- [ ] Each tenant has an owner.
- [ ] Each tenant maps to a documented environment or boundary.
- [ ] Production tenant administrators use MFA.
- [ ] Log streaming is configured before production launch.
- [ ] Configuration promotion path is documented.
