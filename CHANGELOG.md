# Changelog

All notable changes to this skill are documented here.

Follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/) and
[Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.1.0] — 2026-04-19

### Initial release

The first public version. Three commands, three references, three templates.

**Commands**
- `/ux review` — full UX audit of a page, flow or component. Detects
  screen type, applies Nielsen 10 and cognitive-load checks, scores
  /100, produces a three-band priority list.
- `/ux critique` — short punchy feedback (5 observations max) — 2 that
  work, 3 that hurt, with heuristic references.
- `/ux improve` — 2-3 concrete improvement proposals with tradeoffs
  and expected impact.

**References**
- `heuristics.md` — Nielsen 10 usability heuristics revisited for 2026
  product UX, with per-screen checklists (landing, form, dashboard,
  listing, detail).
- `cognitive-load.md` — Miller 7±2, Hick's law, Fogg B=MAT, and the
  practical principles for reducing mental load.
- `patterns.md` — UX patterns and anti-patterns library, grouped by
  context (forms, navigation, data display, onboarding, errors).

**Templates**
- `review-report.md` — full audit output format.
- `critique-report.md` — focused feedback format.
- `improvement-proposal.md` — change proposal format.

### Supported inputs
React (.tsx, .jsx), Vue, Svelte, Astro, plus screenshots and verbal
descriptions of a flow.

[0.1.0]: https://github.com/cherifskr/ux-review/releases/tag/v0.1.0
