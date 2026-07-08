# Troubleshooting

Use this page to diagnose common Auth0 implementation and operations issues. Start with the symptom, identify the affected tenant, application, connection, and time window, then correlate Auth0 logs with application logs.

## Common issues

| Symptom | Likely cause | Next step |
| --- | --- | --- |
| Callback mismatch | Redirect URI is not registered exactly | Compare the runtime URL with the application callback setting |
| Invalid audience | Client requested the wrong API audience | Check the `audience` parameter and API identifier |
| Missing claims | Action, mapping, or provider claim configuration did not run as expected | Review Action logs and provider attribute mappings |
| Federation failure | Identity provider metadata, certificate, assignment, or claim issue | Check connection logs and provider-side logs |
| MFA failures spike | Policy change, factor outage, or user enrollment issue | Review recent releases and MFA event logs |
| API returns 401 | Missing, invalid, expired, or wrong-audience token | Decode safely and validate expected claims without logging secrets |
| API returns 403 | Token is valid but missing required permission | Review scopes, roles, and API authorization code |
| Logout does not clear session | App, Auth0, and upstream provider sessions differ | Test each session layer separately |

## Triage workflow

1. Identify affected users and applications.
2. Confirm the tenant and environment.
3. Check recent configuration or application releases.
4. Search Auth0 logs for the same time window.
5. Compare expected and actual redirect, token, or provider settings.
6. Reproduce in a non-production environment if possible.
7. Document root cause and update runbooks.

## Data to collect

- Tenant and environment.
- Application client ID or name.
- Connection name.
- User identifier, if safe and allowed by policy.
- Timestamp and timezone.
- Error code and event ID.
- Recent release or configuration change.

## Escalation guidance

Escalate to the identity platform team when the issue affects shared tenant configuration, multiple applications, federation, MFA, or log delivery. Escalate to the application team when the issue is isolated to callback handling, session handling, or API authorization code.
