# Write Your First Action

A production Action should be small, explicit, and easy to test. The first useful enterprise Action usually adds a namespaced claim or denies access when required metadata is missing.

## Basic Action shape

Most Actions export an async function. The function receives an `event` object with transaction context and an `api` object with methods that modify flow behavior.

```javascript
exports.onExecutePostLogin = async (event, api) => {
  const namespace = 'https://example.com/claims';

  api.idToken.setCustomClaim(`${namespace}/tenant_id`, event.organization?.id || null);
  api.accessToken.setCustomClaim(`${namespace}/tenant_id`, event.organization?.id || null);
};
```

## Minimal production example

This Action adds organization context to tokens only when the login happened in an organization context. It avoids writing null claims and keeps the namespace stable.

```javascript
exports.onExecutePostLogin = async (event, api) => {
  const namespace = 'https://identity.example.com';

  if (!event.organization) {
    return;
  }

  api.idToken.setCustomClaim(`${namespace}/organization_id`, event.organization.id);
  api.idToken.setCustomClaim(`${namespace}/organization_name`, event.organization.display_name);

  api.accessToken.setCustomClaim(`${namespace}/organization_id`, event.organization.id);
};
```

## Add a defensive access check

Use `api.access.deny` when the login must stop. Keep the error reason clear for operations, but avoid exposing sensitive internal details.

```javascript
exports.onExecutePostLogin = async (event, api) => {
  if (!event.user.email_verified) {
    api.access.deny('email_not_verified', 'Verify your email address before signing in.');
  }
};
```

## Development workflow

1. Create the Action in a non-production tenant.
2. Select the correct trigger.
3. Add the code.
4. Test with representative users and applications.
5. Add secrets only through Action secrets.
6. Create a version.
7. Bind the version to the flow.
8. Monitor real-time logs.

## First Action checklist

- [ ] Trigger matches the use case.
- [ ] Code has no hard-coded secrets.
- [ ] Custom claims use a stable namespace.
- [ ] Denial behavior is intentional and tested.
- [ ] Logs contain no sensitive data.
- [ ] Version is promoted through the approved process.
