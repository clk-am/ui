# CLAUDE.md — clk-am/ui (CC entry point)

Design system implementation: tokens + Web Components for clk.am admin UIs.

**Strategic context lives in `clk-am/strat`.** This repo is the impl. Read [`clk-am/strat:design-system/plan.md`](https://github.com/clk-am/strat/blob/main/design-system/plan.md) for the canonical milestone-by-milestone plan; mirror is in this repo's `v0.1.0` GitHub milestone with one issue per § N.

## Where to find current state

| Question | Answer |
|----------|--------|
| What's the next milestone? | GitHub milestone `v0.1.0` — pick lowest-numbered open issue |
| What's the canonical spec for this milestone? | `clk-am/strat:design-system/plan.md` § N (linked from each issue) |
| Why this framework / scope / license? | ADRs in `clk-am/strat:decisions/0004` through `0007` |
| Cross-product context (platform phases) | `clk-am/strat:ROADMAP.md` |

## Conventions

- **Stack**: pnpm workspace, TypeScript strict, Lit 3.x (Shadow DOM), Vite (build), Vitest (test), Storybook 8 (docs).
- **npm scope**: `@clkam/*` canonical per ADR 0004. Never publish under `@clk-am/*` (reserved squat-protection).
- **Lit pinned exact**: no `^` or `~` on the Lit version in `packages/components/package.json`.
- **Tokens-first**: every theme value via `var(--clk-*)`. No hardcoded colors / spacing / fonts / radii.
- **Components**: Lit + Shadow DOM by default; vanilla escape hatch only for <30 LOC stateless primitives.
- **Attribute mapping**: kebab-case attributes require `@property({ attribute: 'kebab-name' })`.

## Commands

| Action | Command |
|--------|---------|
| Install | `pnpm install` |
| Run Storybook locally | `pnpm storybook` (http://localhost:6006) |
| Build all packages | `pnpm build` |
| Run tests | `pnpm test` |
| Lint | `pnpm lint` |
| Type-check | `pnpm tsc --noEmit` |
| Pack tarball for local consumer test | `pnpm --filter @clkam/ui-tokens pack` |
| Link to consumer | `pnpm --filter @clkam/ui-tokens link --global` |

## Anti-patterns

| Don't | Do |
|-------|-----|
| Hardcode hex / px / rem in component CSS | Use `var(--clk-color-*)`, `var(--clk-space-*)` |
| Override `createRenderRoot` to skip Shadow DOM | Keep default — encapsulation is intentional (ADR 0005) |
| Edit milestone scope without updating the linked plan § | Plan in strat is canonical; PR there first, then mirror |
| Add a new architectural pattern without ADR | Open ADR in `clk-am/strat:decisions/` first |

## Cross-repo references

- Plan / PRD / ideation / ADRs: `clk-am/strat:design-system/`
- Master Phase tracker: `clk-am/strat:ROADMAP.md`
- Project board: https://github.com/orgs/clk-am/projects/1
- Consumer (initial migration target): `clk-am/analytics`
- Infra (DNS / CF Pages / CF Access for storybook.clk.am): `clk-am/infra`
