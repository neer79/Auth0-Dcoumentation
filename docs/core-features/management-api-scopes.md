# Management API Scopes

The Auth0 Management API uses scopes to authorize administrative automation. Management API credentials must be treated as privileged because they can read or change tenant configuration and user data.

## Scope design principles

- Grant the minimum scopes required for the automation job.
- Use separate Machine to Machine applications per environment and purpose.
- Prefer read-only scopes for reporting and inventory.
- Avoid reusing broad automation clients for unrelated jobs.
- Review scopes whenever automation responsibilities change.

## Common scope groups

| Automation purpose | Typical scope pattern |
| --- | --- |
| Tenant inventory | Read applications, APIs, connections, actions, users as needed |
| User reporting | Read users and user metadata only when approved |
| Application provisioning | Create or update clients and related grants |
| API provisioning | Create or update resource servers and scopes |
| Connection automation | Create or update connections and enabled clients |
| Log stream automation | Read or manage log stream configuration |
| Evidence capture | Mostly read-only scopes plus export destination access |

## Credential storage

Management API clients require secure handling:

- Store client ID and secret in an approved vault.
- Restrict who can read production credentials.
- Rotate credentials on a schedule and after suspected exposure.
- Monitor token issuance for automation clients.
- Disable unused automation clients.

## Dangerous automation patterns

- Using one all-powerful Management API client for every pipeline.
- Granting write scopes to read-only reporting jobs.
- Running destructive scripts without dry-run output.
- Logging Management API tokens or secrets.
- Sharing production credentials across environments.

## Review checklist

- [ ] Each automation client has an owner.
- [ ] Scopes are documented and justified.
- [ ] Credentials are environment-specific.
- [ ] Secrets are stored in a vault.
- [ ] Token exchange and Management API activity are monitored.
