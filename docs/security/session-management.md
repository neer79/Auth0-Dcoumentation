# Session management

Session management controls how long users remain signed in and how logout behaves across applications and identity providers.

## Session layers

| Layer | Description |
| --- | --- |
| Auth0 session | Session maintained by Auth0 for single sign-on behavior |
| Application session | Session maintained by the application after authentication |
| Identity provider session | Session maintained by the upstream enterprise provider |
| Refresh token session | Long-lived client ability to obtain new tokens |

## Design decisions

- Idle timeout.
- Absolute timeout.
- Remembered device policy.
- Single sign-on expectations.
- Logout behavior across Auth0, application, and identity provider sessions.
- Refresh token lifetime and rotation.

## Enterprise guidance

- Align session lifetimes with application risk.
- Keep privileged applications shorter-lived.
- Test logout behavior with every federation provider.
- Document when logout does not end the upstream identity provider session.
- Monitor unusual refresh token reuse or session anomalies.

## Validation checklist

- [ ] Idle and absolute timeouts are documented.
- [ ] Application session expiration is aligned with Auth0 policy.
- [ ] Logout behavior is tested.
- [ ] Refresh token settings are reviewed.
- [ ] High-risk applications have appropriate session constraints.
