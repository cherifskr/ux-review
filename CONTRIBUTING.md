# Contributing to UX Review

Thanks for considering a contribution. This skill stays focused and
opinionated — not every suggestion will land, but every thoughtful
issue is welcome.

## Before you open a PR

**Open an issue first** for anything larger than a typo fix. Describe:
- The real use case you're trying to solve (not a hypothetical)
- How it affects people using the skill today
- Your proposed approach at a high level

Two minutes of alignment saves hours of rework.

## What we accept

- 🟢 **Bug fixes** — wrong output from a procedure, broken examples.
- 🟢 **Better wording** — especially for the prose in SKILL.md and
  commands. Both French and English are welcome.
- 🟢 **New screen-type checklists** — for specific contexts (checkout,
  settings page, pricing page, error pages, etc.) that merit their own
  UX patterns.
- 🟢 **References updates** — keeping frameworks current, adding legit
  citations (with links to the primary source).

## What we don't accept (today)

- 🔴 **New top-level commands** — `review` / `critique` / `improve`
  cover the 80%. Open a discussion first if you think otherwise.
- 🔴 **Tooling / scripts** — planned for v2.0 (paid).
- 🔴 **LLM-specific tuning** — the skill must work on any Claude
  version without tweaks.

## Style guide

- **Prose**: French (primary audience is francophone designers/devs).
- **Tech terms**: English (`CTA`, `above the fold`, `empty state`,
  `hero`, `onboarding`, `conversion` — industry names stay).
- **Voice**: warm, senior, and opinionated. Not preachy.
- **Citations**: when you invoke a principle, link or name the source
  (Nielsen, Fogg, Miller, Krug, Norman…).
- **Examples**: always concrete. Name a real pattern, show a real diff.

## How to test a change

Before submitting:

1. Symlink the repo into your skills folder:
   ```bash
   ln -s $(pwd) ~/.claude/skills/ux-review
   ```
2. Restart Claude Code.
3. Run `/ux review` on at least **two different screens** (a landing
   and a form, for example).
4. Verify the output still respects the SKILL.md principles.

## Commit messages

Follow [Conventional Commits](https://www.conventionalcommits.org/):

```
feat(references): add patterns for onboarding friction audit
fix(review): detect forms without inline validation
docs(readme): clarify install instructions for Windows
```

## Code of conduct

Be kind, be specific, assume good intent.

## Questions?

- 📧 [contact@cherifsikirou.com](mailto:contact@cherifsikirou.com)
- 💼 [LinkedIn](https://www.linkedin.com/in/cherifsikirou/)
- 🐛 [Open an issue](https://github.com/cherifskr/ux-review/issues/new)
