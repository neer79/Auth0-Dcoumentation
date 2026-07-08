# Break Glass Access

Break glass access provides emergency administrative access when normal identity paths fail. It should be rare, monitored, and reviewed after every use.

## Requirements

- Document account purpose and owner.
- Use strong credentials and MFA where possible.
- Store credentials in an approved vault.
- Restrict who can retrieve credentials.
- Alert on credential retrieval and account use.
- Review after every use.

## Use cases

- Enterprise identity provider outage prevents administrator login.
- MFA provider issue blocks normal access.
- Production tenant misconfiguration requires emergency correction.
- Incident response requires immediate access outside standard workflow.

## Operating procedure

1. Declare emergency access need.
2. Obtain approval from incident or security owner.
3. Retrieve credentials from the vault.
4. Perform the minimum required action.
5. Record actions taken.
6. Rotate credentials if required.
7. Complete post-use review.

## Validation checklist

- [ ] Account exists and is tested on schedule.
- [ ] Credentials are vaulted.
- [ ] Retrieval is monitored.
- [ ] Use is reviewed after every event.
- [ ] Access remains limited to emergency scenarios.
