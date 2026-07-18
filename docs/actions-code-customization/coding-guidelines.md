# Action Coding Guidelines

Actions execute in identity flows, so code quality directly affects login, token issuance, user registration, and service authentication. Production Actions should be boring, explicit, and defensive.

## Coding standards

- Use `async` functions and `await` for asynchronous work.
- Validate every optional value from `event` before using it.
- Keep functions short and single-purpose.
- Use constants for namespaces, metadata keys, and allowlists.
- Fail closed only when the business risk requires it.
- Avoid long-running work in login flows.
- Never log credentials, tokens, secrets, or full profiles.

## Safe event access

```javascript
exports.onExecutePostLogin = async (event, api) => {
  const appName = event.client?.name || 'unknown-client';
  const connection = event.connection?.name || 'unknown-connection';

  console.log('post-login-start', {
    client: appName,
    connection,
    user_id: event.user.user_id
  });
};
```

## Avoid unsafe assumptions

Bad pattern:

```javascript
exports.onExecutePostLogin = async (event, api) => {
  const department = event.user.app_metadata.department.toLowerCase();
  api.accessToken.setCustomClaim('department', department);
};
```

Safer pattern:

```javascript
exports.onExecutePostLogin = async (event, api) => {
  const namespace = 'https://identity.example.com';
  const department = event.user.app_metadata?.department;

  if (typeof department !== 'string' || department.length === 0) {
    return;
  }

  api.accessToken.setCustomClaim(`${namespace}/department`, department.toLowerCase());
};
```

## External call pattern

```javascript
async function fetchWithTimeout(url, options, timeoutMs) {
  const controller = new AbortController();
  const timeout = setTimeout(() => controller.abort(), timeoutMs);

  try {
    return await fetch(url, { ...options, signal: controller.signal });
  } finally {
    clearTimeout(timeout);
  }
}

exports.onExecutePostLogin = async (event, api) => {
  const response = await fetchWithTimeout(event.secrets.RISK_API_URL, {
    method: 'POST',
    headers: {
      'content-type': 'application/json',
      authorization: `Bearer ${event.secrets.RISK_API_TOKEN}`
    },
    body: JSON.stringify({ user_id: event.user.user_id })
  }, 1500);

  if (!response.ok) {
    api.access.deny('risk_service_unavailable', 'Sign-in cannot be completed right now.');
  }
};
```

## Review checklist

- [ ] Optional fields are checked before access.
- [ ] External calls have timeout behavior.
- [ ] Logs are sanitized.
- [ ] Secrets use `event.secrets`.
- [ ] Denial messages are user-safe.
- [ ] Token claims are namespaced and approved.
