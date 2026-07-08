# Azure AD

Use Azure AD, now Microsoft Entra ID, federation when workforce, partner, or customer users authenticate through a Microsoft identity tenant.

## Recommended protocol

Use OIDC for new integrations unless SAML is required by policy or compatibility constraints. SAML remains common for enterprise federation where existing metadata and claims processes are already established.

## Required inputs

- Entra tenant ID.
- Application registration or enterprise application owner.
- Client ID and secret or certificate when using OIDC.
- Redirect URI for the Auth0 connection.
- Required claims and optional group claims.
- Logout requirements.

## Configuration sequence

1. Create or identify the Entra application registration.
2. Configure redirect URI values required by Auth0.
3. Configure claims, groups, or app roles if needed.
4. Create the Auth0 enterprise connection.
5. Restrict the connection to approved applications or organizations.
6. Test assigned and unassigned user behavior.
7. Document ownership and escalation contacts.

## Claims guidance

- Prefer stable identifiers over email as permanent user keys.
- Decide whether group claims are needed or whether authorization should be managed elsewhere.
- Keep emitted claims minimal.
- Document any transformation logic in Actions.

## Validation checklist

- [ ] Login succeeds for an assigned user.
- [ ] Login fails predictably for an unassigned user when assignment is required.
- [ ] Required claims are present.
- [ ] Logout behavior is understood.
- [ ] Provider owner and metadata are documented.
