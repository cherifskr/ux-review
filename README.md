# UX Review — Claude Code Skill

> A senior product designer in your CLI. Audits pages, flows and components against Nielsen heuristics, cognitive load theory, and real-world product UX patterns.

[![License: MIT](https://img.shields.io/badge/License-MIT-black.svg)](./LICENSE)
[![Claude Code Skill](https://img.shields.io/badge/Claude%20Code-Skill-ff6b35.svg)](https://docs.claude.com/claude-code)
[![Version](https://img.shields.io/badge/version-0.1.0-blue.svg)](./CHANGELOG.md)

---

## What it does

Three commands that turn Claude into a **senior UX partner** reviewing your work:

```bash
/ux review src/app/page.tsx            # full UX audit of a page or flow
/ux critique src/components/Hero.tsx   # short punchy senior feedback
/ux improve "the checkout flow"        # 2-3 reasoned improvement proposals
```

Works on **React / Vue / Svelte / Astro** source files, plus screenshots and verbal descriptions. Zero config.

## Why this exists

Most AI code assistants review your **code**. Very few review your **experience**.

A component can ship clean TypeScript, zero warnings, perfect tests — and still confuse the hell out of users. A page can pass every lint rule and kill 40% of your conversion because the CTA hierarchy is wrong.

This skill closes that gap. It applies the frameworks senior product designers actually use when they review a screen:

- **Nielsen's 10 Usability Heuristics** — the classics that still run the industry
- **Fogg Behavior Model** (B = MAT) — behavior = motivation × ability × trigger
- **Cognitive load theory** — Miller 7±2, Hick's law, working memory limits
- **Gestalt principles** — how humans group and prioritize visual info
- **Real product patterns** — common anti-patterns we all ship by accident

Opinionated output, prioritized action plan, French prose with English for the tech.

## Quick start

### 1. Install

**Global** (recommended):

```bash
git clone https://github.com/cherifskr/ux-review ~/.claude/skills/ux-review
```

**Per project**:

```bash
git clone https://github.com/cherifskr/ux-review .claude/skills/ux-review
git add .claude/skills/ux-review
git commit -m "chore(skills): add ux-review"
```

### 2. Restart Claude Code

### 3. Run it

```bash
/ux review src/app/resources/page.tsx
/ux critique Hero.tsx
/ux improve "the onboarding form feels too long"
```

Or just say it in natural language — the skill triggers on keywords like « review UX », « feedback design », « comment améliorer ce flow ».

## Structure

```
ux-review/
├── SKILL.md                  # entry point for Claude Code
├── commands/
│   ├── review.md             # /ux review — full audit
│   ├── critique.md           # /ux critique — focus feedback
│   └── improve.md            # /ux improve — change proposals
├── references/
│   ├── heuristics.md         # Nielsen 10 + per-screen checklists
│   ├── cognitive-load.md     # Miller, Hick, Fogg, reduction principles
│   └── patterns.md           # UX patterns + anti-patterns library
└── templates/
    ├── review-report.md      # audit output format
    ├── critique-report.md    # focus feedback format
    └── improvement-proposal.md  # change proposal format
```

Each file is legit standalone reading — a compact UX handbook even without Claude.

## What you get from each command

### `/ux review`

A markdown report with:
- **Screen type detected** (landing, form, dashboard, listing, detail)
- **Score /100** across 5 axes (clarity, hierarchy, friction, feedback, a11y)
- **Issues sorted 🔴 / 🟡 / 🟢** — blocking / friction / polish
- For each issue: the heuristic violated, user impact, proposed fix, effort estimate
- "What I'd ship this week" — the 3 highest-ROI items

### `/ux critique`

A punchy feedback — **5 observations max**:
- 2 things that work (genuinely — not empty praise)
- 3 things that hurt (specific, actionable)
- No scoring, no formalism. Pure senior gut reaction backed by principles.

### `/ux improve`

2-3 concrete improvement proposals with:
- The problem solved
- Tradeoffs of each option
- Recommended option with clear rationale
- Mockup-level description (no code yet)
- Expected impact on key metrics (conversion, time-to-task, errors)

## Philosophy

Six principles the skill applies to every output:

1. **Detect the screen type first.** A landing and a dashboard follow different rules — always.
2. **Cite your frameworks.** Every flagged issue names the principle (Nielsen #X, Hick's law, Fogg…).
3. **Speak conversion, not aesthetics.** "This loses 30% of clicks" beats "it's ugly".
4. **Prioritize in 3 bands.** 🔴 blocking / 🟡 friction / 🟢 polish. No flat lists.
5. **Propose, don't decree.** Every issue comes with a proposed fix (before/after).
6. **Mobile-first in your head.** Half your users are on phones. Always check that filter.

## Pairs perfectly with `design-system-pro`

```bash
/ds audit        # system health — tokens, variants, consistency
/ux review       # experience health — clarity, friction, hierarchy
```

Use both. `/ds audit` finds hardcoded hex and orphan components. `/ux review` finds confusion and bad hierarchy. Different problems, same quality bar.

## Roadmap

**v0.1.0** ← you are here
- [x] `/ux review` — full UX audit
- [x] `/ux critique` — focused feedback
- [x] `/ux improve` — improvement proposals

**v1.0 (free)**
- [ ] Screen-specific templates (auth flow, checkout, empty states, error pages)
- [ ] Screenshot-to-review via Claude vision
- [ ] i18n: English version of the SKILL.md

**v2.0 (paid)**
- [ ] Conversion-optimized landing review with quantified impact estimates
- [ ] Onboarding flow analyzer (friction per step, drop-off prediction)
- [ ] A/B test variant suggestions backed by literature
- [ ] Heatmap reading (pair with Hotjar/Plausible exports)

## Contributing

See [CONTRIBUTING.md](./CONTRIBUTING.md). TL;DR:
- Open an issue before big changes
- Keep the FR/EN split (prose French, tech English)
- Don't add commands — each one should solve a real pain
- Test on your own project before submitting

## License

MIT © 2026 Chérif Sikirou

## Who built this

I'm **Chérif Sikirou**, Sr. Product Designer & DS Specialist based in Abidjan. 8+ years shipping products in SaaS, e-commerce, fintech. I built this skill because writing the same UX audit doc over and over was killing my weekends.

- 🌐 [cherifsikirou.com](https://cherifsikirou.com)
- 💼 [LinkedIn](https://www.linkedin.com/in/cherifsikirou/)
- 📧 [contact@cherifsikirou.com](mailto:contact@cherifsikirou.com)

---

