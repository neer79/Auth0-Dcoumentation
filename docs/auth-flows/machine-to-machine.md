# Machine to Machine

Machine to Machine applications use the client credentials flow to obtain access tokens for APIs. This pattern is for service identities, not user authentication.

## When to use

Use Machine to Machine applications when:

- A backend service calls another API without user interaction.
- A scheduled job needs scoped access to an API.
- A deployment or automation service needs limited administrative access.

Do not use this flow for browser, mobile, or user-facing sign-in.

## Security controls

- Store client credentials in an approved secrets manager.
- Grant only required API scopes.
- Rotate credentials on a defined schedule.
- Monitor token exchange volume and failed token requests.
- Disable unused service clients.

## Scope design

Use narrow scopes that map to service responsibilities. Prefer `reports:write` over a broad `admin` scope when the service only writes reports.

## Operational checklist

- [ ] Service owner is documented.
- [ ] Secret storage location is documented.
- [ ] Scopes are reviewed by the API owner.
- [ ] Rotation procedure is tested.
- [ ] Monitoring exists for token request anomalies.
