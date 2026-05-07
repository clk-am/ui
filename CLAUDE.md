# CLAUDE.md — clk-am/ui (CC entry point)

Design system implementation: tokens + Web Components for clk.am admin UIs.

The implementation plan is tracked via the GitHub milestone `v0.1.0` and its 8 issues. Each issue is self-contained: title in the form `§N — Title`, body carries summary, files-to-create, dependencies, acceptance criteria, and out-of-scope items. Pick the lowest-numbered open issue and read its body — that's the canonical spec for the next chunk of work.

## Where to find current state

| Question | Answer |
|----------|--------|
| What's the next milestone? | GitHub milestone `v0.1.0` — pick lowest-numbered open issue |
| What's the spec for this milestone? | The issue body (acceptance criteria + files-to-create + dependencies are inline) |
| Why this framework / scope / license? | See `README.md` § Architecture choices for the inlined rationale |
| Cross-product context | Project board (link below) |

## Conventions

- **Stack**: pnpm workspace, TypeScript strict, Lit 3.x (Shadow DOM), Vite (build), Vitest (test), Storybook 8 (docs).
- **npm scope**: `@clkam/*` canonical. Never publish under `@clk-am/*` (reserved squat-protection only).
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
| Override `createRenderRoot` to skip Shadow DOM | Keep default — encapsulation is intentional |
| Edit milestone scope without coordinating with the maintainer | Open an issue or PR raising the change first |
| Add a new architectural pattern without raising it first | Discuss in an issue or PR before implementing |

## References

- Public design-system milestones: https://github.com/clk-am/ui/milestone/1
- Project board: https://github.com/orgs/clk-am/projects/1
