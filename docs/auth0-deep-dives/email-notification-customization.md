# Email Notification Customization

Auth0 email templates shape account verification, password reset, enrollment, invitation, and other lifecycle communications. Treat them as part of the production user experience and security model.

## Common email templates

| Template type | Purpose |
| --- | --- |
| Verification email | Confirm user email ownership |
| Welcome email | Introduce account or application access |
| Password reset | Allow users to reset credentials |
| Change password | Notify or support credential changes |
| Blocked account | Communicate account blocking or security action |
| MFA enrollment or reset | Support MFA lifecycle where applicable |
| Organization invitation | Invite B2B users to join an organization |
| Passwordless email | Deliver OTP or login link for passwordless flows |

## Email provider decisions

- Use Auth0 default email provider only for development or low-risk use if it meets requirements.
- Use a custom SMTP or email provider for production when deliverability, branding, or compliance requires it.
- Assign ownership for sender domain, SPF, DKIM, DMARC, and bounce handling.
- Monitor delivery failures and user support volume.

## Template design rules

- Use approved sender name and domain.
- Keep subject lines clear and non-alarming.
- Avoid exposing internal tenant names.
- Include support contact or help link when appropriate.
- Keep security-sensitive links short-lived.
- Localize content when required by user population.
- Do not include secrets or full tokens in visible content.

## Change process

1. Draft content with product, support, and security owners.
2. Validate links and expiry behavior.
3. Test rendering across common email clients.
4. Test localization and fallback language.
5. Promote template changes through configuration process.
6. Monitor delivery and support tickets after release.

## Checklist

- [ ] Sender domain is approved.
- [ ] Template owner is documented.
- [ ] Security language is reviewed.
- [ ] Links and expiration are tested.
- [ ] Deliverability is monitored.
- [ ] Localization requirements are met.
