# Monitoring

Monitoring detects authentication failures, anomalous behavior, integration issues, and operational drift. Auth0 events should be treated as both reliability and security signals.

## Key signals

- Login success and failure rates.
- MFA enrollment, challenge, and failure events.
- Federation errors by connection.
- Token exchange failures.
- Action execution errors.
- Suspicious IP or anomaly events.
- Log stream delivery failures.

## Alert examples

| Alert | Trigger |
| --- | --- |
| Federation outage | Error rate for a connection exceeds baseline |
| Credential attack | Failed login volume spikes for a user population |
| MFA issue | MFA failure rate increases after release |
| Action failure | Action error count exceeds threshold |
| Log pipeline issue | Log stream delivery stops or lags |

## Dashboard requirements

Dashboards should show:

- Authentication volume over time.
- Error rate by application and connection.
- Top failure reasons.
- MFA activity.
- High-risk events.
- Recent production changes.

## Validation checklist

- [ ] Production logs reach the monitoring platform.
- [ ] Alerts have owners.
- [ ] Alert thresholds are reviewed periodically.
- [ ] Runbooks link from alerts.
- [ ] Release events can be correlated with login failures.
