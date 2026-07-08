# Universal Login

Universal Login provides the hosted authentication experience for applications. In enterprise deployments it should be treated as shared user-facing infrastructure.

## Design goals

- Provide a consistent login experience across applications.
- Support custom domains and enterprise branding.
- Preserve secure Auth0-hosted authentication flows.
- Support MFA, federation, password reset, and error handling.
- Meet accessibility and localization requirements.

## Production requirements

- Use a custom domain for production-facing applications.
- Apply approved brand elements and content.
- Validate layout across desktop and mobile devices.
- Test MFA enrollment and challenge paths.
- Test federation error and password reset paths.
- Keep customization source-controlled where possible.

## Content considerations

Login copy should be brief and operationally useful. Avoid exposing internal tenant names, infrastructure names, or security implementation details.

## Validation scenarios

- First-time login.
- Returning user login.
- MFA enrollment.
- MFA challenge.
- Password reset.
- Federated identity provider error.
- Logout and re-login.
- Mobile viewport.

## Accessibility checklist

- [ ] Text contrast meets organizational accessibility standards.
- [ ] Form labels are clear.
- [ ] Error messages identify the corrective action.
- [ ] Login works without custom browser extensions.
- [ ] Localization requirements are documented.
