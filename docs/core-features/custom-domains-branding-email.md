# Custom Domains, Branding, and Email

Custom domains, branding, and email templates shape the user-facing Auth0 experience. In enterprise environments, these settings must align with security, support, accessibility, and brand standards.

## Custom domains

A custom domain lets users interact with Auth0 through an organization-controlled domain instead of the default Auth0 tenant domain.

## Custom domain decisions

| Decision | Guidance |
| --- | --- |
| Domain name | Use a stable login domain such as `login.example.com` |
| Certificate ownership | Assign owner for certificate lifecycle and DNS validation |
| Environment domains | Use separate domains or subdomains for non-production where needed |
| Application migration | Plan callback and issuer changes carefully |
| Token issuer | Ensure APIs validate the expected issuer after custom domain adoption |

## Branding controls

Branding can include logo, colors, login page text, and related hosted pages. Keep branding accessible and supportable.

- Use approved logos and color contrast.
- Keep login page text concise.
- Avoid exposing internal tenant names or infrastructure details.
- Validate mobile and desktop rendering.
- Test all enabled login flows after branding changes.

## Email templates

Auth0 may send emails for verification, password reset, blocked account flows, invitations, or other lifecycle actions.

Document:

- Sender domain and address.
- Template owner.
- Supported languages.
- Legal or compliance text.
- Link expiration expectations.
- Support contact information.

## Production checklist

- [ ] Custom domain DNS and certificate ownership are documented.
- [ ] Applications use the intended domain and issuer.
- [ ] Branding passes accessibility review.
- [ ] Email templates are reviewed by security and support owners.
- [ ] Password reset and verification emails are tested.
