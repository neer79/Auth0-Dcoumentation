# Deployment and release

Use controlled release practices for Auth0 configuration changes. Identity releases can affect many applications at once, so releases need clear scope, validation, and rollback plans.

## Release types

| Type | Examples | Approval |
| --- | --- | --- |
| Standard | New application, API scope, connection assignment | Pull request review |
| High risk | MFA policy, token lifetime, federation metadata | Security and platform approval |
| Emergency | Production outage remediation | Incident commander approval, post-change reconciliation |

## Release process

1. Create a change request or pull request.
2. Validate configuration in non-production.
3. Review security and operational impact.
4. Approve production deployment.
5. Apply configuration.
6. Run post-deployment validation.
7. Record release evidence.

## Rollback planning

Every production release should identify:

- Previous known-good configuration.
- Reversal steps.
- Expected user impact.
- Validation after rollback.
- Communication owner.

## Production checklist

- [ ] Change scope is documented.
- [ ] Affected applications are identified.
- [ ] Validation plan is complete.
- [ ] Rollback plan is complete.
- [ ] Release evidence is stored.
