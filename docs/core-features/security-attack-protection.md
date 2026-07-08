# Security and Attack Protection

Auth0 security features help reduce account compromise, credential attacks, and risky authentication behavior. These controls should be part of the enterprise security baseline, not optional afterthoughts.

## Security feature areas

| Feature area | Purpose |
| --- | --- |
| MFA | Require additional factors for administrators, risky access, or protected apps |
| Attack protection | Detect or reduce brute force, suspicious IP, and credential stuffing behavior |
| Breached password detection | Identify credentials known to be compromised where supported |
| Bot detection | Reduce automated abuse against login and signup flows where available |
| Session controls | Limit how long users remain authenticated |
| Refresh token rotation | Reduce replay risk for long-lived sessions |
| Signing keys | Support token signature validation and key rotation |

## Enterprise baseline

- Enforce MFA for dashboard administrators.
- Enable appropriate attack protection features for user-facing tenants.
- Monitor failed login spikes and anomaly events.
- Review password policy for database connections.
- Use short-lived access tokens.
- Rotate client secrets and signing keys according to policy.
- Require approval for disabling security protections.

## Attack signals to monitor

- Repeated failed logins for one account.
- Failed logins across many accounts from one source.
- Breached password detections.
- MFA challenge failures or bypass patterns.
- Signup or password reset abuse.
- Token exchange anomalies.

## Response guidance

1. Confirm affected tenant, application, connection, and user population.
2. Check whether a recent release changed authentication behavior.
3. Review Auth0 logs and upstream provider logs.
4. Contain affected accounts, IP ranges, clients, or connections when appropriate.
5. Preserve evidence for incident response.
6. Tune controls after post-incident review.

## Validation checklist

- [ ] Administrator MFA is enforced.
- [ ] Attack protection settings are reviewed.
- [ ] Password and recovery policies are documented.
- [ ] Risk events are monitored.
- [ ] Security exceptions have owners and expiry dates.
