# Security Policy

The app handles wallet connections and displays financial state. Take it seriously.

## Reporting a vulnerability

**Do not open a public issue for a security problem.**

Use GitHub's private vulnerability reporting on this repository (Security tab: Report a vulnerability), or reach the maintainers through a private channel.

Include:

1. Affected page, component, or flow, with commit hash or release tag.
2. Deployment (preview or production URL).
3. Steps or proof of concept.
4. Your assessment of impact and severity.

## Our commitment

| Severity | Acknowledgment | Fix target |
|---|---|---|
| Critical (funds or keys at risk) | 48 hours | As fast as safely possible |
| High | 72 hours | 30 days |
| Medium | 1 week | 60 days |
| Low | 2 weeks | Best effort, next release |

We credit reporters in release notes unless you prefer to stay anonymous.

## Scope

In scope: this repository's pages, API routes, wallet connection flows, environment handling, and the indexer client.

Out of scope: the contracts repository (report there), third party services (Vercel, anchors, RPC providers), and missing security headers on preview deployments unless they reach production.

## Current status

Pre alpha on testnet. No real funds are at risk; hygiene is practiced as if there were.
