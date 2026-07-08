# MFA

Multi-factor authentication reduces account takeover risk for administrators and users. MFA policy should balance risk, usability, recovery, and operational support.

## Required MFA scenarios

- Auth0 dashboard administrators.
- Users accessing high-risk applications.
- Users performing privileged operations.
- Suspicious or anomalous login activity where adaptive controls are used.

## Design decisions

| Decision | Consideration |
| --- | --- |
| Enrollment timing | At first login, before high-risk access, or during onboarding |
| Factor types | Push, OTP, WebAuthn, SMS, or email depending on risk policy |
| Recovery | Define help desk and self-service recovery process |
| Exceptions | Require approval, expiration, and compensating controls |
| Monitoring | Alert on repeated MFA failures and bypass events |

## Implementation guidance

- Enforce administrator MFA before production launch.
- Prefer phishing-resistant factors for privileged users when available.
- Test enrollment and recovery before broad rollout.
- Communicate policy changes before enforcement.
- Monitor enrollment drop-off and support volume.

## Validation checklist

- [ ] Administrators are challenged for MFA.
- [ ] Recovery process is documented.
- [ ] MFA failure events are visible in monitoring.
- [ ] Exceptions have owners and expiration dates.
