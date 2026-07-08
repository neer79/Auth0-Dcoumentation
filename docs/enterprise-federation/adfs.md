# ADFS

Use ADFS federation when users authenticate through on-premises Active Directory Federation Services. ADFS integrations usually require careful certificate, metadata, and claim rule management.

## Required inputs

- ADFS federation metadata URL or file.
- Relying party trust identifier.
- Assertion consumer service URL.
- Signing certificate and expiration date.
- Required claim rules.
- ADFS operations owner and escalation contact.

## Configuration sequence

1. Exchange metadata between Auth0 and ADFS administrators.
2. Create or update the relying party trust in ADFS.
3. Configure claim issuance rules.
4. Configure the Auth0 SAML enterprise connection.
5. Restrict the connection to approved applications.
6. Test login with representative users.
7. Document certificate renewal procedure.

## Common failure modes

| Symptom | Likely cause |
| --- | --- |
| Invalid signature | Certificate mismatch or expired certificate |
| Audience mismatch | Incorrect relying party identifier |
| Missing user attributes | Claim rules are incomplete |
| Intermittent failures | Clock skew or load-balanced ADFS inconsistency |

## Validation checklist

- [ ] Metadata is current.
- [ ] Certificate expiration is tracked.
- [ ] Claim rules are documented.
- [ ] Login works for test users in expected groups.
- [ ] ADFS errors are visible to the operations team.
