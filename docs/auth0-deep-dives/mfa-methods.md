# MFA Methods

Auth0 MFA adds a second verification step during authentication. Factor availability can depend on tenant plan and configuration, so validate the approved factor list for your tenant before rollout.

## Auth0 MFA factor catalog

| Factor | User experience | Enterprise guidance |
| --- | --- | --- |
| Push notification | User approves a push in an authenticator app | Good usability; monitor push fatigue and denied pushes |
| SMS notification | User receives a code by text message | Convenient but weaker for high-risk users due to SIM swap risk |
| Voice notification | User receives a spoken code by phone call | Useful fallback; monitor abuse and telephony reliability |
| One-time password | User enters TOTP from authenticator app | Common baseline; works offline after enrollment |
| WebAuthn security key | User uses a hardware key | Strong phishing-resistant factor for administrators and high-risk users |
| WebAuthn device biometrics | User uses platform authenticator such as fingerprint or face recognition | Strong user experience where device support exists |
| Email notification | User verifies through email | Useful fallback, weaker if email account is compromised |
| Cisco Duo | Delegated MFA through Duo | Useful when enterprise already standardizes on Duo |
| Recovery codes | One-time backup codes | Required for recovery; protect and monitor use |

## MFA rollout models

| Model | Use when | Notes |
| --- | --- | --- |
| Mandatory MFA | Administrators, privileged apps, regulated access | Strongest posture, higher support load |
| Conditional MFA | Risk, app, connection, or organization context determines challenge | Requires good testing and monitoring |
| Step-up MFA | Sensitive operations require additional assurance | App/API must request or enforce step-up context |
| Adaptive MFA | Risk signals influence whether MFA is required | Review events and false positives |

## Factor selection guidance

- Use WebAuthn/security keys or platform biometrics for administrators where practical.
- Use OTP as a broad baseline factor when hardware keys are not available.
- Use SMS and voice cautiously for high-risk user populations.
- Use recovery codes only for recovery, not normal authentication.
- Use Duo when the enterprise has existing Duo policy and support processes.

## Enrollment and recovery

Plan these before enforcement:

- Enrollment timing and grace period.
- Required number of enrolled factors.
- Factor reset approval process.
- Help desk verification procedure.
- Lost device process.
- Break glass administrator process.

## Monitoring signals

- MFA enrollment failures.
- Challenge failures.
- Push denied events.
- Recovery code use.
- Factor reset events.
- MFA policy changes.

## Rollout checklist

- [ ] Approved factors are documented.
- [ ] Pilot group completed enrollment.
- [ ] Recovery process is tested.
- [ ] Help desk scripts are ready.
- [ ] Monitoring and alerts are configured.
- [ ] Exceptions have owner and expiry.
