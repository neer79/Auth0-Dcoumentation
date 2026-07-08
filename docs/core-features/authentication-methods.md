# Authentication Methods

Auth0 supports multiple authentication methods through connections and protocols. Enterprise platforms should approve methods explicitly and document where each is allowed.

## Supported method categories

| Category | Examples | Enterprise use |
| --- | --- | --- |
| Database | Username and password stored by Auth0 | Customer identity, fallback, or non-federated users |
| Enterprise | OIDC, SAML, Azure AD, ADFS, Okta, Google Workspace | Workforce, partner, and customer federation |
| Social | Google, GitHub, Apple, and other social providers | Consumer or developer-facing scenarios |
| Passwordless | Email or SMS codes and links | Low-friction scenarios with strong abuse monitoring |
| Passkeys and WebAuthn | Phishing-resistant authentication methods | High-assurance user authentication where supported |
| Machine identity | Client credentials | Service-to-service access without a user |

## Selection criteria

Use the authentication method that matches the user population and risk:

- Workforce users usually authenticate through enterprise federation.
- Customer users may use database, social, passwordless, passkeys, or customer-managed federation.
- Partner users often require organization-aware enterprise federation.
- Services should use Machine to Machine applications, not user credentials.

## Database authentication controls

- Enforce password policy.
- Enable breached password protection where appropriate.
- Define password reset and account recovery procedures.
- Monitor failed login spikes.
- Require MFA for high-risk use cases.

## Passwordless controls

- Monitor code request volume and failures.
- Rate-limit abuse-prone channels.
- Define expiry time and retry behavior.
- Be cautious using SMS for high-risk authentication.

## Enterprise validation checklist

- [ ] Approved authentication methods are documented by user population.
- [ ] Every connection has an owner.
- [ ] Recovery and support process is documented.
- [ ] Abuse and failure events are monitored.
- [ ] High-risk applications require stronger authentication.
