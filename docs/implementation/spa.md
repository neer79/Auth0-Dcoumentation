# Single Page Applications

Single page applications should use Authorization Code with PKCE. They are public clients and must not store client secrets.

## Configuration requirements

- Application type is Single Page Application.
- Callback URLs are exact and environment-specific.
- Logout URLs are exact and approved.
- Allowed web origins match the deployed application origins.
- API audience and scopes are documented when calling APIs.

## Implementation guidance

- Use an Auth0-supported SPA SDK when possible.
- Use Authorization Code with PKCE.
- Avoid implicit flow for new applications.
- Avoid storing tokens in local storage unless a documented risk decision approves it.
- Prefer in-memory token storage and refresh token rotation where supported.
- Handle login_required and consent_required errors explicitly.

## Validation scenarios

- First-time login.
- Returning user login.
- Token renewal.
- API call with valid scope.
- API denial with missing scope.
- Logout and re-login.
- Browser refresh.
- Expired session.

## Production checklist

- [ ] PKCE is used.
- [ ] No client secret is present in frontend code.
- [ ] Redirect and logout URLs are exact.
- [ ] Token storage approach is documented.
- [ ] API authorization failures are handled gracefully.
