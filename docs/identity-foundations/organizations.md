# Organizations

Organizations represent business customers, partners, or other B2B boundaries. They help model tenant-aware login, membership, branding, invitations, and identity provider routing.

## When to use Organizations

Use Organizations when applications need:

- Customer- or partner-specific membership.
- Organization-specific branding.
- Organization-specific enterprise identity provider routing.
- Invitation-based onboarding.
- Tenant-aware authorization or audit records.

## Design decisions

| Decision | Guidance |
| --- | --- |
| Organization identifier | Use a stable identifier that does not change with display name |
| Membership source | Decide whether membership is managed manually, through APIs, or through provisioning |
| Connection assignment | Restrict organization connections to approved identity providers |
| Branding | Define whether customer-specific branding is allowed |
| Authorization | Decide how organization membership maps to roles or permissions |

## Metadata model

Common organization metadata includes:

- Customer or partner identifier.
- Contract or account status.
- Support tier.
- Region or data residency marker.
- Default connection or login routing hint.

## Operational controls

- Review organization creation permissions.
- Monitor invitation abuse and failed organization login attempts.
- Define organization deactivation procedures.
- Keep membership lifecycle aligned with customer lifecycle systems.

## Validation checklist

- [ ] Organization naming and identifier standards are documented.
- [ ] Membership lifecycle is defined.
- [ ] Organization connections are restricted.
- [ ] Tenant-aware audit requirements are documented.
