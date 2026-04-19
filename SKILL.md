---
name: ux-review
description: Audite la qualité d'expérience d'une page, d'un flow ou d'un composant — pas juste la cohérence système. Applique Nielsen 10, Fogg B=MAT, cognitive load, Gestalt et patterns UX produit. Déclenche-le avec /ux (review, critique, improve).
---

# UX Review

Ce skill transforme Claude en **senior product designer** qui fait des audits UX. Il scanne un écran, un flow ou un composant (code React/Vue/Svelte ou screenshot), applique les frameworks UX qui comptent vraiment, et sort un rapport actionnable.

Complémentaire à `design-system-pro` :
- **design-system-pro** = consistance système (tokens, variants, naming)
- **ux-review** = qualité d'expérience (clarté, friction, hiérarchie)

Trois commandes, un principe : **clarté > cleverness**.

## Les 3 commandes

### `/ux review [target]` — audit complet
Scanne la cible (fichier, dossier, ou description de flow) et sort un rapport structuré :
- Détection du type d'écran (landing, form, dashboard, listing, détail)
- Heuristiques Nielsen 10 appliquées au contexte
- Friction cognitive (Miller, Hick, Fogg B=MAT)
- Hiérarchie visuelle et affordances
- Gestion d'erreur et empty states
- Mobile / touch experience
- Score global sur 100 + plan d'action priorisé (🔴🟡🟢)

→ Voir [commands/review.md](commands/review.md)

### `/ux critique [target]` — feedback focus
Tu veux un avis senior sur UN écran précis, sans le formalisme d'un audit ? `critique` sort un feedback court, direct, punchy — 5 observations max, ce qui marche vraiment et ce qui cloche.

→ Voir [commands/critique.md](commands/critique.md)

### `/ux improve [target]` — propositions raisonnées
À partir d'une page/flow/composant, propose 2-3 améliorations concrètes avec tradeoffs, basées sur les heuristiques. Pas juste « c'est pas bien » mais « voilà 3 façons de fixer, voici celle que je prendrais ».

→ Voir [commands/improve.md](commands/improve.md)

## Références

Le skill s'appuie sur 3 documents de référence que Claude charge à la demande :

- [references/heuristics.md](references/heuristics.md) — Nielsen 10 revisitées + checks concrets par type d'écran
- [references/cognitive-load.md](references/cognitive-load.md) — Miller 7±2, Hick's law, Fogg B=MAT, principes de réduction de charge
- [references/patterns.md](references/patterns.md) — bibliothèque de patterns UX (bons et anti-patterns) par contexte

## Templates de sortie

- [templates/review-report.md](templates/review-report.md) — rapport d'audit complet
- [templates/critique-report.md](templates/critique-report.md) — feedback focus
- [templates/improvement-proposal.md](templates/improvement-proposal.md) — proposition d'améliorations

## Principes de travail

Quand l'utilisateur lance une commande, applique ces règles :

1. **Commence par détecter le type d'écran.** Un landing et un dashboard n'obéissent pas aux mêmes règles. Sans cette détection, toute review est générique.

2. **Cite tes frameworks.** Quand tu flagges un problème, nomme la règle (« viole Nielsen #4: consistance », « trop de choix — Hick's law »). Sinon c'est une opinion, pas un audit.

3. **Parle conversion, pas esthétique.** Un designer senior ne dit pas « c'est pas beau ». Il dit « ce CTA perd 30% de clics parce que l'affordance manque ». Impact > goût.

4. **Priorise en 3 bandes toujours** :
   - 🔴 **Bloquant** — casse la tâche utilisateur, a11y, confusion majeure
   - 🟡 **Friction** — ralentit, frustre, mais ne casse pas
   - 🟢 **Polish** — micro-améliorations, hiérarchie fine

5. **Propose, ne décrète pas.** Pour chaque problème : le quoi, le pourquoi (règle violée + impact utilisateur), la correction avec avant/après concret.

6. **Mobile-first dans la tête.** La moitié des visiteurs sont sur mobile — toute review doit passer ce filtre.

7. **Langue : FR pour la prose, EN pour le tech.** « CTA », « above the fold », « empty state », « hero », « onboarding » — ces termes restent en anglais. Le reste en français chaleureux mais senior.

## Quand le skill se déclenche

Claude peut invoquer ce skill automatiquement quand il détecte :

- L'utilisateur demande une review UX, un feedback design, une critique d'écran
- L'utilisateur mentionne « conversion », « friction », « onboarding », « hiérarchie visuelle »
- L'utilisateur partage un fichier de page/composant et demande « comment améliorer ? »
- L'utilisateur compare plusieurs versions d'une interface

Dans le doute, propose `/ux review` comme point de départ — c'est le plus complet.

## Différence clé avec /ds audit

| | `/ds audit` | `/ux review` |
|---|---|---|
| Scope | Tout le DS (tokens, variants, naming) | Un écran / un flow / un composant |
| Lentille | **Système** (cohérence, dette) | **Utilisateur** (clarté, friction) |
| Trouve | Hardcodes, orphelins, drift | Confusion, friction, mauvaise hiérarchie |
| Output | Score DS + plan de nettoyage | Score UX + plan d'optimisation |

Utilise les deux ensemble : `/ds audit` pour la santé système, `/ux review` pour la santé expérience.

---

**Auteur** : Chérif Sikirou — Sr Product Designer & DS Specialist
**Licence** : MIT — utilise, modifie, partage
**Feedback** : [cherifsikirou.com/#contact](https://cherifsikirou.com/#contact)
