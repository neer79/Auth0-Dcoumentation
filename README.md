# Enterprise Auth0 Guide

Professional MkDocs Material documentation for designing, implementing, and operating Auth0 in enterprise environments.

## What is included

- MkDocs Material configuration with search, navigation, admonitions, tabs, and Mermaid diagram support.
- A structured documentation tree modeled after enterprise cloud documentation patterns.
- Auth0-specific core feature documentation for applications, APIs, connections, Universal Login, custom domains, Actions, MFA, attack protection, logs, SDKs, and the Management API.
- Deep-dive Auth0 solution playbooks for architecture, business use cases, integration patterns, application onboarding, customer IdP onboarding, Actions, MFA methods, passwordless, email/SMS customization, custom error pages, key rotation, tenant setup, and ongoing support.
- GitHub Actions workflow for publishing to GitHub Pages.
- Contribution, changelog, and roadmap documentation.

## Local development

```powershell
python -m pip install -r requirements.txt
mkdocs serve
mkdocs build --strict
```

## Publishing

The included GitHub Actions workflow builds the site with `mkdocs build --strict` and deploys the generated `site/` directory to GitHub Pages from the default branch.


