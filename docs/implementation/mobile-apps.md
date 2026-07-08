# Native and Mobile Apps

Native and mobile applications should use Authorization Code with PKCE and platform security capabilities. They are public clients and cannot protect embedded secrets.

## Configuration requirements

- Application type is Native Application.
- Redirect URI follows platform guidance.
- Logout URLs and allowed origins are configured where applicable.
- Refresh token rotation is reviewed for the user experience.
- API scopes are limited to required capabilities.

## Implementation guidance

- Use the system browser instead of embedded web views.
- Use platform secure storage for tokens.
- Do not embed client secrets.
- Support device lock, biometric, or application-level reauthentication for high-risk actions.
- Handle offline and token renewal scenarios carefully.

## Validation scenarios

- First install and login.
- Token renewal.
- Logout.
- Reinstall behavior.
- Device migration or backup restore behavior.
- Lost or compromised device process.

## Production checklist

- [ ] PKCE is used.
- [ ] System browser flow is used.
- [ ] Token storage is platform secure.
- [ ] Refresh token settings are approved.
- [ ] Mobile release notes include identity changes.
