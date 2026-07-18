# Actions Patterns

Actions let teams customize Auth0 flows with code. Use patterns so customization stays understandable, testable, and supportable.

## Pattern catalog

| Pattern | Trigger | Purpose | Risk |
| --- | --- | --- | --- |
| Add custom claims | Post Login, M2M | Put approved context into tokens | Token bloat or sensitive claims |
| Enforce business access | Post Login | Deny access based on org, risk, or lifecycle status | Login outage if dependency fails |
| Normalize profile | Post Login | Standardize user attributes from multiple IdPs | Incorrect identity data |
| Organization authorization hints | Post Login | Add org roles or tenant context | Stale authorization if not validated server-side |
| Service token enrichment | M2M | Add service metadata to access tokens | Overbroad service privilege |
| Audit notification | Post Login or lifecycle | Send events to downstream system | Latency or duplicate events |
| Migration bridge | Post Login | Temporary legacy lookup or profile migration | Long-term hidden dependency |

## Custom claims pattern

Use custom claims when applications or APIs need identity context that is not part of the standard token profile.

Rules:

- Use a stable namespace where required.
- Add only claims with clear consumers.
- Document source, owner, and lifetime of each claim.
- Keep values compact.
- Do not put secrets or sensitive internal data in tokens.

## Access enforcement pattern

Actions can deny login, but denial logic should be simple and well-tested. Complex authorization belongs in APIs or applications.

Good uses:

- Block deactivated customer account.
- Require organization membership.
- Deny unsupported connection for a specific app.
- Trigger MFA for a risky scenario.

Risky uses:

- Calling fragile external services synchronously on every login.
- Embedding large entitlement calculations in Actions.
- Using Actions as a replacement for API authorization.

## External API calls

If an Action calls an external service:

- Set a timeout.
- Decide fail-open or fail-closed behavior.
- Monitor latency and failures.
- Avoid calling services that are not highly available.
- Cache or move data into Auth0 metadata where appropriate.

## Release process

1. Write Action code in source control.
2. Review code and dependencies.
3. Store secrets as Action secrets.
4. Test success, denial, timeout, and exception paths.
5. Deploy to non-production trigger.
6. Promote version to production.
7. Monitor logs after deployment.

## Checklist

- [ ] Action pattern and trigger are documented.
- [ ] Token claims are approved.
- [ ] External dependencies are resilient.
- [ ] Secrets are not hard-coded.
- [ ] Runtime failures are monitored.
