# MFA and Adaptive Controls

Auth0 MFA and adaptive controls help increase assurance during authentication. Enterprise teams should define when MFA is always required, when it is risk-based, and how users recover access.

## MFA factor categories

| Factor category | Examples | Enterprise notes |
| --- | --- | --- |
| One-time passwords | Authenticator app codes | Common baseline factor |
| Push notifications | Mobile authenticator push | Usable, but monitor push fatigue risk |
| WebAuthn/passkeys | Platform or roaming authenticators | Strong phishing-resistant option where supported |
| SMS or voice | Phone-based factors | Use cautiously for high-risk scenarios |
| Email | Email-based verification | Useful in some flows, weaker as a second factor |

## MFA policy models

| Model | Use when | Tradeoff |
| --- | --- | --- |
| Always-on MFA | Administrators and high-risk apps | Strong assurance, higher friction |
| Conditional MFA | Risk, application, connection, or organization context matters | Requires careful testing |
| Step-up MFA | Only sensitive operations need stronger proof | Application must request or enforce step-up context |
| Adaptive MFA | Risk signals influence challenge behavior | Requires monitoring and policy review |

## Enrollment decisions

- When are users enrolled?
- Which factors are allowed?
- Are backup factors required?
- Who can reset factors?
- How are lost devices handled?
- Are break glass procedures required for administrators?

## Operational signals

Monitor:

- MFA enrollment failures.
- MFA challenge failures.
- Repeated denied pushes or failed OTP attempts.
- Recovery events.
- Factor reset events.
- Changes to MFA policy.

## Validation checklist

- [ ] Administrator MFA is enforced.
- [ ] Factor policy is documented.
- [ ] Enrollment and recovery flows are tested.
- [ ] Step-up or conditional rules are tested per app.
- [ ] MFA events are monitored.
