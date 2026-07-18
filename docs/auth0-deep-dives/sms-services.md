# SMS Services

SMS is used in Auth0 for passwordless OTP, some MFA factors, and phone-based user verification scenarios. SMS is convenient but has security, deliverability, cost, and regional compliance tradeoffs.

## SMS use cases

| Use case | Description |
| --- | --- |
| SMS passwordless | User receives one-time code to sign in |
| SMS MFA | User receives code as a second factor |
| Voice fallback | User receives a spoken code by phone call |
| Account recovery | Phone channel helps recover access where approved |

## Provider decisions

- Use an approved SMS provider or integration path for production.
- Define sender ID, regional routing, and supported countries.
- Monitor delivery rates, latency, and failures.
- Track cost and abuse risk.
- Define compliance requirements for phone number processing.

## Security risks

- SIM swap and number takeover.
- SMS interception or forwarding.
- OTP phishing.
- SMS pumping and cost abuse.
- Delivery failures in specific regions.

## Mitigations

- Prefer stronger factors for administrators and high-risk access.
- Rate-limit OTP requests.
- Monitor request spikes by IP, phone prefix, application, and geography.
- Use short OTP lifetimes.
- Add fraud detection for suspicious SMS volume.
- Provide alternative recovery paths.

## Support runbook inputs

- User phone number status.
- Region and carrier if available.
- Time of OTP request.
- Application and tenant.
- Delivery provider status.
- Recent rate-limit or attack-protection events.

## Checklist

- [ ] SMS use case is approved.
- [ ] Provider ownership is documented.
- [ ] Regional delivery is tested.
- [ ] Abuse monitoring is enabled.
- [ ] High-risk users have stronger alternatives.
