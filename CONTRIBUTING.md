# Contributing to clk-am/ui

## External contributions

External PRs are not currently accepted. CLA wiring (cla-assistant.io + Harmony CLA) is a hard gate of the v0.1.0 § 1 Prerequisites milestone but is **deferred per maintainer decision**. Bug reports via [GitHub issues](https://github.com/clk-am/ui/issues) are welcome.

When external contributions are accepted, the CLA bot will be wired before any PR can merge.

## Local dev workflow

```bash
git clone https://github.com/clk-am/ui.git
cd ui
pnpm install
pnpm storybook  # local Storybook on http://localhost:6006
pnpm build      # builds all packages
pnpm test       # runs vitest across packages
```

Consumers can link this repo into their local checkout for live iteration:

```bash
# In clk-am/ui:
pnpm --filter @clkam/ui-tokens build
cd packages/tokens && pnpm link --global

# In clk-am/analytics (or any consumer):
pnpm link --global @clkam/ui-tokens
```

## Conventions

- **Commits**: feature-focused subjects, conventional-commits style (`feat:`, `fix:`, `refactor:`, `docs:`).
- **Components**: Lit 3.x with Shadow DOM by default. Vanilla escape hatch only for <30 LOC, stateless primitives.
- **Lit version**: pinned exact (no `^` or `~`). Bumps require a PR with bundle-size delta.
- **Attribute mapping**: kebab-case attributes require explicit `@property({ attribute: 'delta-period' })` declaration. Lit's default lowercases the property name (e.g., `deltaPeriod` → `deltaperiod`).
- **Styles**: `static styles = css`...`` with `--clk-*` tokens for theme values, `::part()` for restylable internal anchors, slots for content composition.
- **Tokens**: every theme value goes through `var(--clk-*)`. No hardcoded colors, spacing, fonts, or radii in component source.

## Browser support

The design-system policy is "last 2 majors of Chromium / Firefox / Safari". The `adoptedStyleSheets` technical floor is Chromium 73 / Firefox 101 / Safari 16.4 — every browser inside the policy window sits well above this floor.

If a consumer ships to a browser below the floor (out-of-policy), Lit injects a `<style>` element inside the shadow root, which under strict CSP requires `style-src 'unsafe-inline'`, a nonce, or a hash.

## Architectural changes

Architectural deviations require a documented decision before implementation — examples: switching framework, changing the npm scope, removing Shadow DOM. Open an issue first, ping the maintainer, and we'll capture the decision. Component-level decisions (new component shape, new prop) do NOT need this — discuss in the PR.

## Code of conduct

This project adopts the [Contributor Covenant 2.1](./CODE_OF_CONDUCT.md).
