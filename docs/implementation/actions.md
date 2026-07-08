# Actions

Actions customize Auth0 flows through managed extensibility points. They are powerful and should be governed like production code.

## Common use cases

- Add custom claims to tokens.
- Normalize user profile attributes.
- Enforce conditional access logic.
- Call external enrichment services.
- Integrate with audit or risk systems.

## Design principles

- Keep Actions small and focused.
- Avoid unnecessary external calls in the login path.
- Use secrets storage for Action credentials.
- Handle external service timeouts and errors.
- Version and review Action code in source control.
- Monitor Action execution failures.

## Deployment guidance

1. Develop in a non-production tenant.
2. Review code and dependencies.
3. Test success and failure paths.
4. Promote through the standard configuration path.
5. Monitor errors after release.

## Validation checklist

- [ ] Action purpose and trigger are documented.
- [ ] Secrets are stored securely.
- [ ] Dependencies are reviewed.
- [ ] Failure behavior is tested.
- [ ] Execution errors are monitored.
