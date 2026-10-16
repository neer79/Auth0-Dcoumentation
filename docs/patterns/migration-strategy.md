# Migration Strategy

Migration strategy defines how applications, users, identity providers, and operational processes move from existing identity systems to Auth0.

## Migration phases

1. Inventory applications, APIs, identity stores, and user populations.
2. Classify applications by complexity and risk.
3. Select pilot applications.
4. Build shared Auth0 foundations.
5. Migrate applications in waves.
6. Monitor adoption and incidents.
7. Retire legacy identity components.

## Application assessment

| Dimension | Questions |
| --- | --- |
| Protocol | Does the app use OIDC, OAuth, SAML, headers, or custom auth? |
| User population | Workforce, customer, partner, or service identity? |
| Authorization | Where are roles and permissions enforced? |
| Session | How is session lifetime managed today? |
| Risk | What is the impact of login failure? |

## Migration patterns

- Federation first: keep existing identity provider and move applications behind Auth0.
- Application wave: migrate related applications together.
- User migration: migrate user stores in planned batches.
- Parallel run: allow old and new login during a controlled transition.

## Cutover checklist

- [ ] Rollback path is defined.
- [ ] Support team is briefed.
- [ ] Monitoring is active.
- [ ] Pilot users are identified.
- [ ] Legacy configuration retirement is scheduled.

## CIAM platform-specific playbooks

For a detailed Akamai Identity Cloud migration plan, including credential-path decisions, federation, MFA, regional architecture, test scenarios, and operational acceptance, see the [Akamai Identity Cloud to Auth0 Migration Playbook](akamai-aic-to-auth0.md).
