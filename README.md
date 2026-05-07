# clk-am/ui

Design system for [clk.am](https://clk.am) — design tokens + Web Components consumed by the analytics, campaigns, and links admin UIs.

**Status**: pre-v0.1 (in active development). Public, Apache-2.0, from day 1.

## Packages

The repo is a pnpm workspace. Once v0.1.0 ships, the following packages will be published to npm under the `@clkam/*` scope ([ADR 0004](https://github.com/clk-am/strat/blob/main/decisions/0004-npm-scope-clkam.md)):

| Package | Status | Purpose |
|---------|--------|---------|
| `@clkam/ui-tokens` | not yet published | Design tokens (CSS + JSON + TS + Tailwind preset) |
| `@clkam/ui-components` | not yet published | Web Components (Lit 3.x, Shadow DOM) |
| `@clkam/ui-icons` | not yet published | Icon set (Tabler subset) |

## Roadmap

The canonical implementation plan lives in [`clk-am/strat:design-system/plan.md`](https://github.com/clk-am/strat/blob/main/design-system/plan.md). Milestones are mirrored as GitHub issues in this repo, attached to the `v0.1.0` milestone.

For the broader platform context (Phase 1 → Phase 2 → Phase 3), see [`clk-am/strat:ROADMAP.md`](https://github.com/clk-am/strat/blob/main/ROADMAP.md).

## Architecture decisions

This repo follows the architecture decisions captured in [`clk-am/strat:decisions/`](https://github.com/clk-am/strat/tree/main/decisions):

- [ADR 0004](https://github.com/clk-am/strat/blob/main/decisions/0004-npm-scope-clkam.md) — npm scope `@clkam/*` canonical
- [ADR 0005](https://github.com/clk-am/strat/blob/main/decisions/0005-lit-as-component-framework.md) — Lit 3.x as Web Components framework
- [ADR 0006](https://github.com/clk-am/strat/blob/main/decisions/0006-storybook-hosting.md) — Storybook hosting (CF Pages + CF Access)
- [ADR 0007](https://github.com/clk-am/strat/blob/main/decisions/0007-clk-am-ui-public-apache-2-from-day-1.md) — public, Apache-2.0, from day 1

## Browser support floor

`adoptedStyleSheets` API floor: Chromium 73, Firefox 101, Safari 16.4. Browsers below this floor receive an injected `<style>` element inside the shadow root and require `style-src 'unsafe-inline'`, a nonce, or a hash under strict CSP. See `CONTRIBUTING.md`.

## Contributing

See [`CONTRIBUTING.md`](./CONTRIBUTING.md). External contributions are not currently accepted (CLA wiring is parked — see [clk-am/strat#9](https://github.com/clk-am/strat/issues/9)). Bug reports via GitHub issues are welcome.

## Trademark

The names **clkam**, **@clkam**, **clk-am**, and the clkam logo are trademarks of O2CS&I and are NOT licensed under Apache License 2.0. Apache § 6 carve-out applies — descriptive use such as “based on `@clkam/ui-tokens`” in a fork is permitted. Anything beyond § 6 requires written permission. See `NOTICE`.

## License

[Apache License 2.0](./LICENSE) — Copyright 2026 O2CS&I. See `NOTICE` for trademark and contribution notices.
