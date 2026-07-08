# Reference diagrams

This page stores reusable diagrams for enterprise Auth0 architecture, authentication flows, and operations. Keep diagrams in Mermaid so they are reviewable in source control.

## Authentication flow

```mermaid
sequenceDiagram
    participant Browser
    participant App
    participant Auth0
    participant IdP
    Browser->>App: Request protected route
    App->>Auth0: Redirect to /authorize
    Auth0->>IdP: Redirect or protocol exchange
    IdP-->>Auth0: Authentication response
    Auth0-->>App: Authorization code
    App->>Auth0: Exchange code for tokens
    Auth0-->>App: ID token and access token
```

## API authorization flow

```mermaid
flowchart LR
    Client[Client Application] --> Auth0[Auth0 Authorization Server]
    Auth0 --> Token[Access Token]
    Client --> API[Protected API]
    Token --> API
    API --> JWKS[JWKS Key Set]
    API --> Decision[Scope or Permission Decision]
```

## Configuration promotion flow

```mermaid
flowchart LR
    Change[Configuration Change] --> PR[Pull Request]
    PR --> Validate[Static Validation]
    Validate --> Plan[Plan or Diff]
    Plan --> Approve[Approval]
    Approve --> Apply[Apply to Tenant]
    Apply --> Verify[Post-Deployment Verification]
```

## Operations flow

```mermaid
flowchart LR
    Auth0[Auth0 Logs] --> Stream[Log Stream]
    Stream --> SIEM[SIEM]
    SIEM --> Alert[Alert]
    Alert --> Runbook[Incident Runbook]
    Runbook --> Evidence[Incident Evidence]
```

## Diagram maintenance

- Keep diagrams focused on one decision or process.
- Prefer explicit component names over abstract boxes.
- Update diagrams in the same pull request as architecture changes.
- Avoid embedding secrets, tenant names, or internal-only URLs.
