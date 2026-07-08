# Glossary

This glossary defines common terms used across the Enterprise Auth0 Guide.

| Term | Definition |
| --- | --- |
| Access token | Token used by a client to access a protected API. APIs must validate it before use. |
| Action | Auth0 extensibility function that runs at supported points in authentication and token flows. |
| API | Protected resource represented by an Auth0 audience and optional scopes. |
| Application | Client configuration in Auth0 for a web, mobile, SPA, native, or service workload. |
| Audience | Identifier that tells Auth0 which API an access token is intended for. |
| Authorization Code with PKCE | OAuth 2.0 flow recommended for public clients such as SPAs and mobile apps. |
| Client credentials | OAuth 2.0 flow used for service-to-service authentication without a user. |
| Connection | Auth0 configuration for a user store or external identity provider. |
| Custom domain | Organization-owned domain used for Auth0-hosted login and related endpoints. |
| ID token | OpenID Connect token containing authentication information for the client. |
| Identity provider | System that authenticates users, such as Entra ID, ADFS, Okta, or Google Workspace. |
| Issuer | Token claim identifying the authorization server that issued the token. |
| JWKS | JSON Web Key Set used by APIs to validate token signatures. |
| Machine to Machine application | Auth0 application type used by service clients. |
| MFA | Multi-factor authentication, requiring more than one factor to authenticate. |
| Organization | Auth0 construct for B2B customer or partner boundaries, membership, and login routing. |
| Refresh token | Token used by a client to obtain new tokens without interactive login. |
| Scope | Permission string representing an API capability, such as `orders:read`. |
| SCIM | System for Cross-domain Identity Management, used for user and group provisioning. |
| Tenant | Auth0 administrative and runtime boundary for identity configuration. |
| Universal Login | Auth0-hosted login experience used by applications. |
