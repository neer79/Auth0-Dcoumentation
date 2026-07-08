# Organizations and B2B

Organizations model business customers, partners, or other B2B boundaries in Auth0. They support membership, organization-specific login, invitations, branding, and enterprise connection assignment.

## What Organizations provide

- Organization records with identifiers, display names, and metadata.
- User membership in one or more organizations.
- Organization-specific enterprise connections.
- Invitations and onboarding flows.
- Organization-aware login prompts.
- Organization branding in supported login experiences.
- Context that applications can use for tenant-aware behavior.

## Common scenarios

| Scenario | How Organizations help |
| --- | --- |
| Multi-tenant SaaS | Represent each customer account or tenant |
| Partner portal | Separate partner companies and membership |
| Customer-managed identity provider | Attach specific enterprise connections to an organization |
| Delegated administration | Support customer-controlled membership processes where designed |

## Design decisions

- What real-world entity maps to an Auth0 Organization?
- Can a user belong to multiple organizations?
- Who creates organizations?
- Who manages membership?
- Are invitations used?
- Are organization-specific identity providers allowed?
- Does authorization depend on organization role, app role, or both?

## Enterprise controls

- Use stable organization identifiers.
- Track organization owner and support contact.
- Restrict who can create or update organizations.
- Monitor invitation and membership changes.
- Validate organization context in APIs for tenant-scoped data.

## Validation checklist

- [ ] Organization lifecycle is documented.
- [ ] Membership ownership is defined.
- [ ] Organization connection routing is tested.
- [ ] Tenant-aware authorization is enforced server-side.
- [ ] Organization events are auditable.
