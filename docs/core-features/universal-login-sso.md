# Universal Login and SSO

Universal Login is Auth0's hosted login experience. Single sign-on uses the Auth0 session to let users access multiple applications without signing in repeatedly, subject to session and security policy.

## What Universal Login provides

- Centralized login, signup, and password reset experience.
- Integration with database, enterprise, social, and passwordless connections.
- MFA enrollment and challenge flows.
- Organization-aware login experiences.
- Custom domain and branding support.
- Safer authentication handling than embedding credentials in each application.

## SSO behavior

SSO depends on multiple session layers:

| Session | Purpose |
| --- | --- |
| Auth0 session | Enables SSO across applications using the same tenant and domain |
| Application session | Controls access inside the application after login |
| Upstream identity provider session | Controls whether federated users must reauthenticate at the provider |
| Refresh token session | Allows clients to obtain new tokens without interactive login |

## Design decisions

- Which applications should share SSO behavior?
- What idle and absolute session lifetimes are acceptable?
- Should production use a custom domain?
- How should logout behave across applications and upstream identity providers?
- What branding and accessibility requirements apply?
- Are organization-specific login prompts or branding required?

## Enterprise guidance

- Use Universal Login for new applications unless a documented exception exists.
- Use custom domains for production user-facing applications where appropriate.
- Keep branding and text simple, accessible, and supportable.
- Test SSO and logout with every supported application type.
- Document differences between application logout, Auth0 logout, and upstream provider logout.

## Validation checklist

- [ ] Login works for each enabled connection.
- [ ] SSO behavior matches policy.
- [ ] Logout behavior is tested and documented.
- [ ] MFA enrollment and challenge flows work.
- [ ] Custom domain and branding are production-ready.
