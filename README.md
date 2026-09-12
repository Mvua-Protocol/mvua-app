# Mvua Protocol Web

[![CI](https://github.com/mvua-protocol/mvua-app/actions/workflows/ci.yml/badge.svg)](./.github/workflows/ci.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](./LICENSE)

**The web layer of [Mvua Protocol](https://github.com/mvua-protocol/mvua-contracts): parametric climate insurance on Stellar.**

Mvua lets smallholder farmers and climate exposed communities buy micro insurance policies in USDC and get paid automatically when on chain weather data shows a failed season. This app is the window into that protocol: pool dashboards, policy purchase, and a payout explorer, served by Next.js and deployed on Vercel.

> Status: **pre alpha**, in active development. The app currently targets the Stellar testnet against contracts under active development.

## Planned surfaces

| Surface | What it does | Status |
|---|---|---|
| Pool dashboard | TVL, tranche split, premiums, payouts, solvency ratio | planned |
| Policy purchase | Pick region and coverage, pay premium, receive policy certificate | planned |
| Payout explorer | Trigger status per region, payout batches, ledger links | planned |
| Publisher console | Oracle publisher status and fee ledger (read only) | planned |
| Cooperative mode | Batch purchase for farmer groups | planned |
| USSD gateway | Phone first access for feature phones (separate gateway service) | planned |

Implementation starts in Phase 3 of the program roadmap; this repository currently ships governance, CI, and pinned configuration.

## Getting started

Prerequisites: Node.js 22 (see `.nvmrc`), npm 10+, a [Freighter](https://www.freighter.app/) wallet for testnet interaction.

```bash
git clone https://github.com/mvua-protocol/mvua-app
cd mvua-app
nvm use
npm install
cp .env.example .env.local
npm run dev
```

Open [http://localhost:3000](http://localhost:3000).

## Scripts

| Command | What it does |
|---|---|
| `npm run dev` | Start the development server |
| `npm run build` | Production build |
| `npm run lint` | ESLint |
| `npm run typecheck` | TypeScript project check |
| `npm run test` | Unit tests (vitest) |
| `npm run e2e` | Playwright end to end suite (Phase 3 onward) |

## Environment variables

Copy `.env.example` to `.env.local`. Client visible variables are prefixed `NEXT_PUBLIC_` and never contain secrets.

| Variable | Purpose |
|---|---|
| `NEXT_PUBLIC_STELLAR_NETWORK` | `testnet` until mainnet launch |
| `NEXT_PUBLIC_HORIZON_URL` | Horizon endpoint for the active network |
| `NEXT_PUBLIC_SOROBAN_RPC_URL` | Soroban RPC endpoint for the active network |
| `NEXT_PUBLIC_CONTRACT_RISK_POOL` | Deployed risk pool contract ID |
| `INDEXER_API_URL` | Server side indexer endpoint (no secrets here either) |

## Deployment

The app deploys on [Vercel](https://vercel.com):

- **Preview** environment for every pull request.
- **Production** environment tracking `main`, pointed at Stellar testnet until mainnet launch.

Environment variables are managed in the Vercel project settings and mirrored in `.env.example`. Detailed runbook: [`docs/VERCEL.md`](./docs/VERCEL.md).

## Architecture notes

- Contract interaction is isolated in a typed client layer; UI components never call chain SDKs directly.
- The indexer is a lightweight event reader backed by the public read API; the app stays stateless beyond caching.
- Accessibility (WCAG 2.1 AA target) and low bandwidth friendliness are requirements, not afterthoughts: much of our audience is on slow connections.

## Contributing

Read [`CONTRIBUTING.md`](./CONTRIBUTING.md). Good first issues are labeled `good first issue`.

## Security

See [`SECURITY.md`](./SECURITY.md). Never open public issues for vulnerabilities.

## License

[MIT](./LICENSE) (c) the Mvua Protocol contributors.
