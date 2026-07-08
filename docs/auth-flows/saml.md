# SAML

SAML is commonly used for enterprise federation and legacy application integration. Auth0 can act as a service provider to enterprise identity providers or as an identity provider to SAML applications.

## Common use cases

- Federating with ADFS or enterprise SAML identity providers.
- Supporting legacy SaaS or internal applications.
- Exchanging signed assertions between trusted parties.

## Required inputs

| Input | Description |
| --- | --- |
| Entity ID | Unique identifier for the SAML party |
| ACS URL | Assertion consumer service endpoint |
| Metadata URL or file | Configuration exchange document |
| Signing certificate | Certificate used to validate assertions |
| NameID format | Identifier format for the subject |
| Attribute mappings | Claims or attributes sent to the application |

## Security requirements

- Require signed assertions or signed responses according to policy.
- Track certificate expiration and renewal owner.
- Validate clock skew tolerance.
- Minimize attributes sent in assertions.
- Test single logout only when explicitly required.

## Troubleshooting signals

- Invalid signature.
- Expired certificate.
- Incorrect audience or recipient.
- Clock skew errors.
- Missing or malformed NameID.

## Validation checklist

- [ ] Metadata exchange is documented.
- [ ] Certificate expiration is tracked.
- [ ] Attribute mappings are reviewed.
- [ ] Login succeeds for assigned users.
- [ ] Error paths are visible in logs.
