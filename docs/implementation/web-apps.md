# Regular Web Applications

Regular web applications use server-side authentication patterns and can safely use confidential client credentials when secrets are stored correctly.

## Configuration requirements

- Application type is Regular Web Application.
- Client secret is stored in an approved secrets manager.
- Callback and logout URLs are exact.
- Session lifetime is aligned with enterprise policy.
- Required APIs and scopes are documented.

## Implementation guidance

- Use Authorization Code flow.
- Store sessions server-side or in secure encrypted cookies.
- Set secure, HTTP-only, and same-site cookie attributes where applicable.
- Keep client secrets out of application repositories.
- Validate state and nonce values through supported libraries.
- Implement logout for both application and Auth0 sessions where required.

## Validation scenarios

- Login from unauthenticated route.
- Callback handling.
- Session expiration.
- Logout.
- CSRF or state validation failure.
- API access with expected scopes.

## Production checklist

- [ ] Secret is stored outside source control.
- [ ] Session cookie settings are reviewed.
- [ ] Callback and logout URLs are exact.
- [ ] Error handling avoids exposing sensitive data.
- [ ] Application owner is documented.
