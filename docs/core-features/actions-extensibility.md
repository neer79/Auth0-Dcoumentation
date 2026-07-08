# Actions and Extensibility

Actions are Auth0's primary extensibility mechanism for customizing identity flows. They allow teams to run code at supported trigger points, such as login and token issuance.

## Common uses

- Add custom claims to tokens.
- Enforce conditional access checks.
- Normalize profile attributes.
- Call external risk, entitlement, or profile services.
- Deny login under specific business rules.
- Send custom events to downstream systems.

## Trigger considerations

| Trigger area | Typical use |
| --- | --- |
| Login flow | Enforce policy, enrich profile, add claims, control access |
| Machine to Machine flow | Add claims or enforce service access controls |
| Credentials exchange | Customize token-related behavior where supported |
| User lifecycle triggers | Integrate provisioning or notification behavior where available |

## Design principles

- Keep Actions small and purpose-specific.
- Avoid slow external calls in the login path.
- Use timeouts and defensive error handling.
- Store secrets using Action secrets, not hard-coded values.
- Version Action code in source control.
- Test both success and denial behavior.
- Monitor runtime errors.

## Enterprise risk areas

| Risk | Mitigation |
| --- | --- |
| Login outage caused by Action failure | Test failure behavior and keep external dependencies resilient |
| Token bloat from custom claims | Add only required claims and keep values compact |
| Secrets exposure | Use Action secrets and restrict access |
| Unreviewed code changes | Promote Actions through CI/CD and approval workflow |

## Validation checklist

- [ ] Trigger and purpose are documented.
- [ ] Secrets are stored securely.
- [ ] External dependencies are documented.
- [ ] Failure behavior is tested.
- [ ] Runtime errors are monitored.
