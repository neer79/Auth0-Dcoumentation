# SCIM provisioning

SCIM automates user and group lifecycle management between an authoritative identity system and Auth0 or downstream applications. Provisioning complements authentication federation; it does not prove a user is currently authenticated.

## Lifecycle events

- Create user.
- Update user profile.
- Deactivate user.
- Reactivate user.
- Assign group or role membership.
- Remove group or role membership.

## Design decisions

| Decision | Guidance |
| --- | --- |
| Source of truth | Identify the system authoritative for each attribute |
| Matching key | Use a stable immutable identifier where possible |
| Deactivation | Prefer disabling access over deleting records when audit retention matters |
| Group mapping | Keep mappings explicit and reviewed |
| Reconciliation | Define how drift between systems is detected and corrected |

## Operational controls

- Monitor provisioning failures.
- Alert on repeated deactivation failures.
- Run periodic reconciliation reports.
- Test disabled-user behavior end to end.
- Document retry and manual repair procedures.

## Validation checklist

- [ ] User creation is tested.
- [ ] Attribute update is tested.
- [ ] Deactivation blocks access as expected.
- [ ] Group or role mapping is tested.
- [ ] Failed provisioning events are monitored.
