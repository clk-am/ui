# clk-am/ui

Design system for [clk.am](https://clk.am) — design tokens + Web Components consumed by the analytics, campaigns, and links admin UIs.

**Status**: pre-v0.1 (in active development). Public, Apache-2.0, from day 1.

## Packages

The repo is a pnpm workspace. Once v0.1.0 ships, the following packages will be published to npm under the canonical `@clkam/*` scope (the hyphenated `@clk-am/*` scope is reserved as squat-protection only and never published to):

| Package | Status | Purpose |
|---------|--------|---------|
| `@clkam/ui-tokens` | not yet published | Design tokens (CSS + JSON + TS + Tailwind preset) |
| `@clkam/ui-components` | not yet published | Web Components (Lit 3.x, Shadow DOM) |
| `@clkam/ui-icons` | not yet published | Icon set (Tabler subset) |

## Roadmap

The implementation plan is tracked via the [`v0.1.0` GitHub milestone](https://github.com/clk-am/ui/milestone/1) and its 8 issues — each issue carries its own acceptance criteria, files-to-create list, and dependencies inline.

## Architecture choices

Key choices baked into v0.1.0:

- **npm scope `@clkam/*`** — canonical for all packages. Hyphenated `@clk-am/*` reserved as squat-protection only, never published.
- **Lit 3.x with Shadow DOM** — chosen for ergonomic reactive properties past ~5 components, real style encapsulation via `adoptedStyleSheets`, and CSS-custom-property token inheritance through the shadow boundary. Lit version pinned exact (no `^` or `~`); vanilla escape hatch reserved for <30 LOC stateless primitives.
- **Storybook on `storybook.clk.am`** — Cloudflare Pages with Cloudflare Access in front during pre-v1.0 to gate work-in-progress content.
- **Public Apache-2.0 from day 1** — eliminates private-npm friction, unlocks npm provenance attestation from v0.1.0, aligns with industry-standard design-system OSS practice (Material Web, Adobe Spectrum, IBM Carbon — all Apache-2.0). Trademarks retained per Apache § 6 carve-out (see `NOTICE`).

## Browser support floor

`adoptedStyleSheets` API floor: Chromium 73, Firefox 101, Safari 16.4. Browsers below this floor receive an injected `<style>` element inside the shadow root and require `style-src 'unsafe-inline'`, a nonce, or a hash under strict CSP. See `CONTRIBUTING.md`.

## Contributing

See [`CONTRIBUTING.md`](./CONTRIBUTING.md). External contributions are not currently accepted (CLA wiring is parked). Bug reports via GitHub issues are welcome.

## Trademark

The names **clkam**, **@clkam**, **clk-am**, and the clkam logo are trademarks of O2CS&I and are NOT licensed under Apache License 2.0. Apache § 6 carve-out applies — descriptive use such as "based on `@clkam/ui-tokens`" in a fork is permitted. Anything beyond § 6 requires written permission. See `NOTICE`.

## License

[Apache License 2.0](./LICENSE) — Copyright 2026 O2CS&I. See `NOTICE` for trademark and contribution notices.
