# Contributing to Mvua Web

Thank you for helping build the interface to open insurance infrastructure.

## Code of conduct

By participating you agree to the [Code of Conduct](./CODE_OF_CONDUCT.md).

## Development setup

1. Node.js 22 (`.nvmrc` pins the exact version; `nvm use`).
2. `npm install`.
3. `cp .env.example .env.local` and fill in testnet values.
4. `npm run dev` and confirm the app loads before you start changing things.

## How we work

- **Trunk based development.** Branch from `main`, PR back to `main`.
- **Branch naming:** `feat/<topic>`, `fix/<topic>`, `chore/<topic>`, `docs/<topic>`, `test/<topic>`.
- **Commits are conventional:** `type(scope): imperative subject`. Example: `feat(app): add pool solvency widget`. Subject at most 72 characters.
- **One logical change per PR.**
- **Every PR needs tests** for new behavior. A fix without the test that would have caught the bug is not done.
- **CI must be green.** Typecheck, lint, tests, build, commit lint, and secret scan.

## Frontend standards (the short version)

- TypeScript `strict`, no `any`; use `unknown` plus narrowing.
- Contract calls live in the typed client layer; components never touch chain SDKs directly.
- Files `kebab-case.ts`, components `PascalCase`, hooks `useThing`.
- All configuration via validated environment variables; `.env.example` documents every variable.
- Accessibility is a requirement: semantic HTML, labeled controls, keyboard operability.
- Design tokens come from the shared theme; no ad hoc colors or spacing.

## PR checklist

- [ ] Conventional commit title and history
- [ ] Unit tests cover new behavior; `npm run test` passes
- [ ] `npm run lint` and `npm run typecheck` pass
- [ ] `npm run build` succeeds
- [ ] Docs and `CHANGELOG.md` updated (under `[Unreleased]`)
- [ ] No new unpinned dependencies (exact versions only, lockfile committed)
- [ ] No secrets, no personal data in the diff

## Reporting issues

- Bugs: use the bug report template with the network, browser, and commit or tag.
- Vulnerabilities: **never** in public issues. See [SECURITY.md](./SECURITY.md).
- Ideas: use the feature request template. Problem first, then solution.

## Review process

1. Maintainers triage and label within a few days.
2. Review focuses on correctness, tests, accessibility, and conventions.
3. Address comments with new commits; squash merge on approval.
4. First time contributors: start with `good first issue` labels.

## Licensing

By contributing you agree your contributions are licensed under the [MIT License](./LICENSE).
