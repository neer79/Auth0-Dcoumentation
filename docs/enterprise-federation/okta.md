# Okta

Use Okta federation when users authenticate through Okta and applications standardize on Auth0 as the application-facing identity layer.

## Protocol options

| Protocol | Use when |
| --- | --- |
| OIDC | New integrations where modern token-based federation is preferred |
| SAML | Existing enterprise federation process or app assignment model depends on SAML |

## Required inputs

- Okta organization URL.
- OIDC client details or SAML metadata.
- Redirect URI or ACS URL.
- Attribute mappings.
- Group or assignment requirements.
- Okta application owner.

## Configuration sequence

1. Create an Okta OIDC or SAML application.
2. Configure the Auth0 callback or ACS URL.
3. Define attribute and group mappings.
4. Create the Auth0 enterprise connection.
5. Limit connection usage to approved applications or organizations.
6. Assign test users and validate login.

## Governance notes

- Keep group claims small and purposeful.
- Document whether Okta assignments or Auth0 Organizations control access.
- Track secret or certificate lifecycle depending on protocol.

## Validation checklist

- [ ] Assigned users can authenticate.
- [ ] Unassigned users receive expected denial behavior.
- [ ] Required attributes are mapped.
- [ ] Group or role behavior is validated.
- [ ] Provider lifecycle owner is documented.
