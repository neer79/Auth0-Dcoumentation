# Passwordless

Passwordless authentication reduces or removes reliance on memorized passwords. Auth0 supports multiple passwordless approaches, each with different user experience, security, and account lifecycle implications.

## Passwordless methods

| Method | How it works | Use when |
| --- | --- | --- |
| Email OTP | User receives a one-time code by email | Low-friction email-based login is acceptable |
| Email magic link | User selects a link sent to email | Classic magic-link experiences are required and supported by chosen login mode |
| SMS OTP | User receives a one-time code by SMS | Phone number is the primary identifier and risk is acceptable |
| Passkeys | User authenticates with synced passkey credentials | Phishing-resistant, low-friction customer login is desired |
| WebAuthn biometrics | User authenticates with device biometrics | Device support and Universal Login flow are appropriate |
| Social login | User authenticates with a social identity provider | Consumer convenience is more important than enterprise account authority |

## Passwordless connection behavior

Email and SMS passwordless connections are distinct identity sources. A user who signs in with email passwordless may have a different Auth0 identity than a user with the same email in a database, social, or enterprise connection. Plan account linking and duplicate profile handling before production.

## Design decisions

- Is email or phone number a reliable identifier for the user population?
- Are duplicate identities acceptable?
- Is account linking required?
- What is the OTP or link lifetime?
- What rate limits and abuse monitoring are required?
- Which channels are supported by customer support?
- Is passwordless primary login or a secondary recovery path?

## Security considerations

- Email security becomes part of authentication assurance for email passwordless.
- SMS can be vulnerable to SIM swap and interception risk.
- Magic links can be forwarded or opened on a different device than the originating request.
- Passkeys provide stronger phishing resistance but need device/browser support planning.
- OTP and link request endpoints need abuse monitoring.

## Operational checklist

- [ ] Passwordless method is approved for the use case.
- [ ] Duplicate identity and account linking strategy is documented.
- [ ] OTP/link expiry and retry behavior are configured.
- [ ] Email or SMS provider reliability is monitored.
- [ ] Support scripts cover lost access and channel changes.
