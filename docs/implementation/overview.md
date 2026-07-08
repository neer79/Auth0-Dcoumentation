# Implementation overview

Implementation guidance standardizes how applications and APIs integrate with Auth0. The goal is to give application teams approved patterns that are secure by default and easy to support.

## Supported integration types

| Integration | Primary guidance |
| --- | --- |
| Single page application | Authorization Code with PKCE, exact redirect URLs, browser-safe token handling |
| Regular web application | Authorization Code, confidential client, server-side session controls |
| Native or mobile application | Authorization Code with PKCE, system browser, secure platform storage |
| API service | JWT validation, audience enforcement, scopes or permissions |
| Machine to Machine | Client credentials, least-privilege scopes, secret rotation |
| Actions | Source-controlled extensibility with dependency review and monitoring |

## Standard onboarding process

1. Identify application owner and business purpose.
2. Select the approved application type and authentication flow.
3. Define callback, logout, and allowed origin values.
4. Identify required APIs and scopes.
5. Configure application and API resources in non-production.
6. Validate login, token, logout, and error behavior.
7. Promote configuration through the approved release path.
8. Capture owner metadata and operational support notes.

## Production readiness

Application teams must demonstrate:

- Correct authentication flow.
- Secure token handling.
- API token validation where applicable.
- Monitoring for authentication failures.
- Rollback plan for identity configuration changes.
- Documented ownership and support contacts.
