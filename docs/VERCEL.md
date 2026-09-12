# Vercel Deployment Runbook

How the app is deployed. The workflow: preview per PR, production tracking `main`, testnet until mainnet launch.

## One time setup (Phase 3, substep P3.10)

1. Import the `mvua-app` repository into a Vercel project (Vercel GitHub App installed on the repo).
2. Framework preset: Next.js. Build command and output are auto detected.
3. Node.js version: 22.x (matches `.nvmrc`).
4. Add environment variables from `.env.example` in Project Settings: Environment Variables. Values for production and preview can differ (they should not: both point at testnet until mainnet).
5. Deploy. Note the production URL; it becomes the demo link used in project documentation.

## Environments

| Environment | Branch | Network | Purpose |
|---|---|---|---|
| Production | `main` | testnet (later mainnet) | The public app |
| Preview | every PR | testnet | Review and E2E before merge |
| Development | local | testnet | Development |

## Rules

1. Production deploys only from `main`, and `main` only accepts PRs with green CI.
2. Every PR gets a Vercel preview automatically; reviewers verify the change in the preview, not locally only.
3. Environment variable changes are part of a PR: `.env.example` updated in the same change, values applied in Vercel before merge.
4. Never put secrets in `NEXT_PUBLIC_` variables; they ship to the browser.

## After a mainnet contract deployment (Phase 6)

1. Update the `NEXT_PUBLIC_CONTRACT_*` variables to mainnet IDs in Vercel (production and preview).
2. Set `NEXT_PUBLIC_STELLAR_NETWORK=mainnet`.
3. Deploy production and verify the happy path in a browser before announcing.
4. Record the new contract IDs in the repository README table in the same release.

## Rollback

Use Vercel's instant rollback to the previous production deployment, then fix forward with a PR. Never hotfix production from an unreviewed branch.
