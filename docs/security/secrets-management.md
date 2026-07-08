# Secrets management

Application credentials and automation secrets must be protected throughout their lifecycle. Auth0 client secrets, Management API credentials, and provider secrets should never be stored in source control.

## Secret types

- Auth0 application client secrets.
- Management API machine credentials.
- Enterprise identity provider client secrets.
- Terraform provider credentials.
- CI/CD pipeline variables.
- Webhook or log stream credentials.

## Requirements

- Store secrets in an approved secret manager.
- Restrict access to production secrets.
- Rotate secrets on a defined cadence.
- Rotate immediately after suspected exposure.
- Avoid sharing secrets through chat, tickets, or documentation.
- Monitor secret access where supported.

## Rotation procedure

1. Create a replacement secret.
2. Store the replacement in the secret manager.
3. Deploy the consuming application or pipeline update.
4. Validate authentication or automation behavior.
5. Revoke the old secret.
6. Record the rotation event.

## Validation checklist

- [ ] Every confidential client has a documented secret owner.
- [ ] Secret storage location is documented.
- [ ] Rotation procedure is tested.
- [ ] Production secret access is restricted.
- [ ] No secrets are present in repository files.
