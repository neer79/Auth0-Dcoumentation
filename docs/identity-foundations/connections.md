# Connections

Connections define where users authenticate and how identities are made available to applications. They can represent database stores, enterprise identity providers, social providers, or passwordless methods.

## Connection types

| Type | Use for | Enterprise notes |
| --- | --- | --- |
| Database | Auth0-managed username and password users | Define password, MFA, and breach detection policies |
| Enterprise | Azure AD, ADFS, Okta, Google Workspace, SAML, OIDC | Document metadata, certificates, claims, and owner |
| Social | Consumer identity providers | Review privacy, domain restrictions, and support model |
| Passwordless | Email or SMS login | Define rate limits, abuse monitoring, and recovery procedures |

## Application enablement

Connections should be enabled only for approved applications. Broadly enabling every connection for every client makes troubleshooting harder and increases accidental access risk.

## Attribute mapping

Document all mapped attributes:

- Source claim or attribute.
- Auth0 user profile field.
- Normalization or transformation logic.
- Required or optional status.
- Owner of the source data.

## Operational requirements

- Track certificate expiration for SAML connections.
- Monitor federation failures and login error spikes.
- Review connection-to-application assignments regularly.
- Keep metadata exchange procedures documented for enterprise providers.

## Validation checklist

- [ ] Connection owner is documented.
- [ ] Enabled applications are intentional.
- [ ] Attribute mappings are documented.
- [ ] Certificates and metadata have renewal owners.
- [ ] Login failures are visible in monitoring.
