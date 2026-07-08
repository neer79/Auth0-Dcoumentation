# B2B Identity

B2B identity supports partner and customer users who authenticate through external organizations. B2B designs need clear lifecycle ownership because users often sit outside internal HR systems.

## Key questions

- Who owns user invitation and approval?
- Are users provisioned before login or created just in time?
- Can customers manage their own identity providers?
- How are organization roles assigned?
- How are users removed when contracts end?

## Architecture options

| Option | Use when | Tradeoff |
| --- | --- | --- |
| Central invitation | Platform team controls onboarding | Slower customer onboarding |
| Delegated administration | Customer admins manage users | Requires stronger audit and guardrails |
| SCIM provisioning | Customer identity provider manages lifecycle | Requires setup and reconciliation support |
| Just-in-time creation | Fast first login | Needs controls for authorization and domain restrictions |

## Operational requirements

- Define customer administrator responsibilities.
- Monitor invitation and membership changes.
- Review inactive users and stale memberships.
- Document support paths for customer identity provider issues.
- Keep audit records organization-aware.

## Validation checklist

- [ ] User onboarding path is documented.
- [ ] User offboarding path is documented.
- [ ] Organization roles are reviewable.
- [ ] Customer identity provider support process exists.
