# Actions Modules and Dependencies

Actions can use code modules and dependencies, but every dependency becomes part of the login or token issuance runtime. Keep dependencies minimal and reviewed.

## When to use a dependency

Use a dependency when it provides meaningful reliability or security value, such as:

- Validating structured data.
- Calling a vendor SDK that handles signing or retry behavior.
- Formatting or parsing protocol-specific data.

Avoid dependencies for simple tasks that native JavaScript handles well.

## Simple helper module pattern

```javascript
function getNamespace() {
  return 'https://identity.example.com';
}

function hasRole(event, roleName) {
  const roles = event.authorization?.roles || [];
  return roles.includes(roleName);
}

exports.onExecutePostLogin = async (event, api) => {
  if (hasRole(event, 'SupportAdmin')) {
    api.accessToken.setCustomClaim(`${getNamespace()}/support_admin`, true);
  }
};
```

## Dependency governance

| Control | Requirement |
| --- | --- |
| Approval | Dependencies require code review |
| Versioning | Pin dependency versions where possible |
| Purpose | Document why the dependency is needed |
| Security | Check known vulnerabilities before production |
| Size | Avoid heavy packages in login flows |
| Ownership | Assign owner for dependency upgrades |

## Secret handling

```javascript
exports.onExecutePostLogin = async (event, api) => {
  const endpoint = event.secrets.PROFILE_API_URL;
  const token = event.secrets.PROFILE_API_TOKEN;

  if (!endpoint || !token) {
    api.access.deny('missing_action_configuration', 'Sign-in cannot be completed right now.');
  }
};
```

## Dependency failure design

Before adding any package or external API, decide:

- Should login fail if the dependency fails?
- Is cached metadata good enough?
- What is the timeout?
- How will failures be monitored?
- Who owns upgrades and vulnerability fixes?
