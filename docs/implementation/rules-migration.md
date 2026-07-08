# Rules migration

Rules should be migrated to Actions using a controlled plan. Migration is a good opportunity to remove obsolete logic, reduce login latency, and improve governance.

## Migration phases

1. Inventory all Rules.
2. Identify trigger behavior and dependencies.
3. Classify each Rule as migrate, retire, or redesign.
4. Rebuild required logic as Actions.
5. Test in non-production.
6. Promote through the release process.
7. Disable legacy Rules after validation.

## Inventory fields

- Rule name.
- Purpose.
- Trigger behavior.
- External dependencies.
- Secrets used.
- Applications affected.
- Owner.
- Migration decision.

## Risk areas

- Login latency from external service calls.
- Unhandled exceptions that block authentication.
- Differences between Rules and Actions execution context.
- Hidden dependencies on user profile shape.
- Missing secrets or configuration during promotion.

## Validation checklist

- [ ] Equivalent behavior is tested.
- [ ] Failure paths are tested.
- [ ] External dependencies are documented.
- [ ] Legacy Rule disablement has rollback guidance.
- [ ] Monitoring is active during cutover.
