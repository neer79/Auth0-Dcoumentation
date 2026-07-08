# CI/CD

CI/CD pipelines should validate, promote, and release Auth0 configuration changes. Identity changes should be reviewed with the same care as infrastructure changes because they can affect login, API access, and security posture.

## Pipeline stages

```mermaid
flowchart LR
    PR[Pull Request] --> Lint[Lint and Static Checks]
    Lint --> Validate[Policy Validation]
    Validate --> Plan[Plan or Diff]
    Plan --> Approve[Approval]
    Approve --> Apply[Apply]
    Apply --> Verify[Post-Deploy Verification]
    Verify --> Evidence[Release Evidence]
```

## Pull request checks

- Validate Markdown and documentation links for docs changes.
- Validate Auth0 configuration syntax.
- Check callback URLs, logout URLs, and allowed origins against environment rules.
- Check token lifetime and grant type policy.
- Check that secrets are not committed.
- Produce a plan or diff for reviewers.

## Production gates

Production deployments should require:

- Approved pull request.
- Successful validation checks.
- Security review for high-risk controls.
- Named release owner.
- Rollback plan.
- Post-deployment verification.

## Evidence capture

Store release evidence with:

- Commit SHA.
- Approvers.
- Tenant and environment.
- Plan or diff output.
- Deployment timestamp.
- Post-deploy validation result.

## Failure handling

If deployment fails:

1. Stop additional promotion.
2. Preserve logs and pipeline output.
3. Determine whether configuration was partially applied.
4. Roll back or complete remediation.
5. Record the incident or release failure.
