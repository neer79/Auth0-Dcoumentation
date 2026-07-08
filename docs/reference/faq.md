# FAQ

## Should every environment have a separate tenant?

For most enterprises, yes. Separate tenants reduce blast radius and make release validation meaningful. Additional tenant boundaries may be required for regulatory, regional, or business ownership reasons.

## Should APIs trust tokens without validation?

No. APIs must validate issuer, audience, signature, expiration, and required scopes or permissions. Network location or client-side checks are not a substitute for API-side enforcement.

## Should configuration be changed directly in production?

Production dashboard changes should be restricted. Use source-controlled automation for normal changes. Emergency dashboard changes must be documented and reconciled back into source control.

## Can applications share one Auth0 client?

Avoid sharing clients across unrelated applications. Separate clients make ownership, callback URLs, secrets, monitoring, and incident response clearer.

## When should Organizations be used?

Use Organizations for B2B or multi-tenant SaaS scenarios that need customer or partner boundaries, membership, organization-specific login routing, or organization-aware authorization.

## Should group claims be placed in tokens?

Only when needed and reviewed. Large group claims can bloat tokens and create authorization coupling. Prefer purpose-built roles, permissions, or application-side authorization when appropriate.

## How should secrets be stored?

Store client secrets, Management API credentials, provider secrets, and pipeline credentials in an approved secrets manager. Do not commit secrets to repositories or place them in documentation.

## What is the difference between authentication and authorization?

Authentication proves who the user or service is. Authorization decides what that user or service can do. Auth0 can help issue claims and permissions, but APIs and applications must enforce authorization.
