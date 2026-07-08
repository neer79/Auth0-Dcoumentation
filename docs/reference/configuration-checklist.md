# Configuration checklist

Use this checklist before production launch or major production changes. Treat unchecked items as release risks that need an owner, exception, or remediation plan.

## Tenant

- [ ] Tenant owner and backup owner are documented.
- [ ] Production dashboard administrators use MFA.
- [ ] Dashboard roles follow least privilege.
- [ ] Custom domain is configured where required.
- [ ] Log stream is configured and monitored.
- [ ] Emergency access is documented and tested.

## Applications

- [ ] Business and technical owners are documented.
- [ ] Application type matches the workload.
- [ ] Callback URLs are exact and environment-specific.
- [ ] Logout URLs are exact and approved.
- [ ] Allowed web origins are reviewed.
- [ ] Client secrets are stored in an approved secrets manager.
- [ ] Unused grant types are disabled where possible.

## APIs

- [ ] API audience is stable and documented.
- [ ] Scopes are reviewed by the API owner.
- [ ] Access token lifetime is approved.
- [ ] APIs validate issuer, audience, signature, expiration, and scopes.
- [ ] Authorization failures are logged safely.

## Connections

- [ ] Connection owner is documented.
- [ ] Enabled applications are reviewed.
- [ ] Metadata and certificates are tracked.
- [ ] Attribute mappings are documented.
- [ ] Federation failure monitoring is active.

## Security

- [ ] MFA policy is documented.
- [ ] Token storage requirements are documented.
- [ ] Session timeout settings are reviewed.
- [ ] Secrets rotation procedure exists.
- [ ] Break glass access is monitored.

## Operations

- [ ] Release process is defined.
- [ ] Rollback procedure exists.
- [ ] Monitoring dashboards are available.
- [ ] Incident response runbook is linked.
- [ ] Compliance evidence location is documented.
