# Custom Error Pages

Custom error pages improve the user experience when authentication fails or when Auth0 cannot complete a flow. They should guide users without exposing sensitive implementation details.

## Error page goals

- Give users a clear next step.
- Preserve brand trust during failure.
- Avoid leaking tenant configuration, stack traces, or secrets.
- Provide support-friendly correlation information when safe.
- Route users to the correct help path for application, customer, or identity provider issues.

## Common error scenarios

| Scenario | User-facing guidance |
| --- | --- |
| Invalid callback or redirect | Ask user to retry later or contact support; route internal alert to platform team |
| Unauthorized application | Explain access is not enabled for the app |
| Federation failure | Tell user their organization sign-in failed and provide support path |
| MFA failure | Provide recovery or help desk instructions |
| Expired passwordless link | Ask user to request a new link or code |
| Organization access denied | Explain account is not assigned to the requested organization |

## Design rules

- Use plain language.
- Do not display raw OAuth, SAML, or token details to end users.
- Include correlation ID only if it helps support and is safe to expose.
- Use consistent links to support or status pages.
- Keep application-specific errors inside the application where possible.

## Operations integration

Custom error pages should connect to operational workflows:

- Log the error event in Auth0 and application logs.
- Alert on spikes in specific error categories.
- Provide support teams with a troubleshooting map.
- Track which customer, application, or connection is affected.

## Checklist

- [ ] Error copy is reviewed by product and support.
- [ ] Sensitive internal details are hidden.
- [ ] Support path is clear.
- [ ] Error scenarios are tested.
- [ ] Monitoring detects error spikes.
