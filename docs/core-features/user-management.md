# User Management

Auth0 user management includes user profiles, identities, metadata, account lifecycle, invitations, and administrative user operations. In enterprise environments, user management must align with authoritative source systems.

## User profile model

An Auth0 user profile can include:

- Stable user identifier.
- Linked identities from one or more providers.
- Standard profile attributes such as name and email.
- Application metadata used by applications.
- User metadata used for user-managed preferences.
- Multifactor enrollment state.
- Organization memberships.

## Metadata guidance

| Metadata type | Use for | Avoid |
| --- | --- | --- |
| `app_metadata` | Application-controlled authorization or lifecycle attributes | User-editable preferences |
| `user_metadata` | User-managed preferences or low-risk profile data | Security decisions unless validated |

## Lifecycle patterns

| Pattern | Use when | Notes |
| --- | --- | --- |
| Just-in-time creation | Users are created at first login | Requires authorization guardrails |
| Admin-created users | Support or platform team creates accounts | Useful for controlled onboarding |
| SCIM provisioning | External identity system manages lifecycle | Best for enterprise customer or workforce lifecycle |
| Bulk migration | Existing user store moves into Auth0 | Requires password and communication planning |

## Account operations

- Create users.
- Block or unblock users.
- Reset passwords.
- Link and unlink identities.
- Assign organization membership.
- Review MFA enrollments.
- Export user inventory for audit and reconciliation.

## Enterprise controls

- Identify the authoritative source for each user population.
- Avoid manually editing attributes owned by external identity systems.
- Monitor privileged user management actions.
- Define support process for account recovery and identity linking.
- Protect user exports because they may contain personal data.

## Validation checklist

- [ ] User source of truth is documented.
- [ ] Metadata ownership is clear.
- [ ] Deactivation behavior is tested.
- [ ] Account recovery process is approved.
- [ ] User management events are auditable.
