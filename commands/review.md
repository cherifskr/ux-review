# `/ux review [target]` — Audit UX complet

> Scanne une page, un flow ou un composant, et sort un rapport UX priorisé.

## Objectif

Donner à l'utilisateur une **photo honnête** de la qualité d'expérience d'un écran, avec un plan d'action qui tient en une session de 2 heures. Pas 50 pages de théorie — 10 items concrets classés par impact.

## Input

- **Par défaut** : l'utilisateur indique un fichier ou un dossier (`src/app/page.tsx`, `src/components/Hero.tsx`)
- **Description verbale** : « le flow de checkout », « la page de pricing »
- **Screenshot** : image collée dans la conversation (Claude vision)
- **Supports code** : React (.tsx, .jsx), Vue (.vue), Svelte (.svelte), Astro (.astro)

Si rien n'est passé → demander à l'utilisateur quel écran reviewer.

## Process

### 1. Détection du type d'écran (obligatoire)

Avant toute analyse, classifie la cible dans un des 6 types standards :

| Type | Signaux | Règles dominantes |
|---|---|---|
| **Landing** | Hero, CTAs multiples, social proof, témoignages | Clarté proposition + CTA hierarchy + scroll depth |
| **Form** | Inputs, labels, validation, submit | Progressive disclosure + validation inline + error recovery |
| **Dashboard** | Metrics, charts, filters, data density | Density vs clarté + actionabilité + context switching |
| **Listing** | Cards/rows, filters, pagination, sort | Scan rapide + empty state + filters discoverability |
| **Detail** | Titre, corps, primary action, related | Back nav + primary action visible + related content |
| **Flow multi-étapes** | Stepper, « next/back », progress | Orientation + save state + error recovery + escape hatches |

Si ambigu (ex: page qui mix landing + listing), identifie le **goal principal** et utilise ce type comme base, en citant les sous-patterns.

### 2. Lecture ciblée (obligatoire)

- Lis le fichier complet (si code)
- Identifie : headings, CTAs, inputs, empty states, error states, loading states
- Note le stack (React/Vue/…) mais l'analyse est agnostique — c'est l'UX qu'on review, pas le code

Pour une description verbale ou un screenshot : liste ce que tu observes AVANT de commenter (« voici ce que je vois : [...]. Ma lecture: [...] »).

### 3. Scan par axes (appliquer selon le type d'écran)

**A. Clarté de proposition** (surtout landing/flow)
- Hero dit-il QUOI et POUR QUI en 5 secondes ?
- Le H1 est-il orienté bénéfice ou feature ?
- Le sous-titre ajoute-t-il de la valeur ou paraphrase le H1 ?

**B. Hiérarchie visuelle**
- Un seul CTA primaire visible ou plusieurs ?
- L'œil est-il guidé vers l'action principale ?
- Violation Nielsen #8 (aesthetic & minimalist) : trop de bruit visuel qui dilue le focus ?

**C. Friction cognitive** (voir [references/cognitive-load.md](../references/cognitive-load.md))
- Choix excessifs → Hick's law (temps de décision croît avec nombre d'options)
- Champs de form : plus de 5-7 → charge, fragmenter
- Jargon inutile ? (Nielsen #2 : match with real world)
- Abréviations non-explicites ?

**D. Affordances**
- Les boutons ressemblent à des boutons ? (fond, padding, élévation)
- Les liens sont distincts du texte ?
- Les inputs ont un bord visible ? Un focus state clair ?
- Si icônes seules : aria-label ET tooltip visible ?

**E. Feedback & feedback loops** (Nielsen #1 : visibility of system status)
- Loading state présent ? (skeleton > spinner > rien)
- Success state visible après action ?
- Erreurs inline (à côté du champ) ou résumé perdu en haut ?

**F. Empty states & edge cases**
- Que voit l'utilisateur quand la liste est vide ?
- Zero data state : message + action ou juste vide ?
- Error global : recovery path clair ?

**G. Mobile / touch**
- Touch targets ≥ 44px ?
- Thumb zone respectée ? (actions importantes en bas de l'écran)
- Pas de hover-only feedback (survol impossible au tactile)
- Responsive réel ou juste "pas cassé" ?

**H. A11y concrète** (complémentaire à `/ds audit` mais d'un angle UX)
- Contraste texte/fond lisible ?
- Focus-visible présent ?
- Ordre de tab logique ?
- Labels associés aux inputs ?
- Informations pas **uniquement** par la couleur ?

**I. Trust & social proof** (surtout landing, checkout, pricing)
- Preuve sociale placée **avant** le CTA ou après ?
- Logos clients / testimonials / metrics : crédibles (specific > vague) ?
- Sécurité/paiement : signaux visibles ? (https, lock icon, badges)

**J. Micro-interactions & polish**
- Transitions > 0 mais < 400ms (sinon c'est lent) ?
- Animations respectent `prefers-reduced-motion` ?
- Hover states subtils ou criards ?

### 4. Score sur 100

| Axe | Poids | Notation |
|---|---|---|
| Clarté de proposition | 20 | Clair en 5s = 20, vague = 5, incompréhensible = 0 |
| Hiérarchie visuelle | 15 | 1 CTA primaire évident = 15, confus = 5 |
| Friction cognitive | 15 | Fluide = 15, surcharge = 0 |
| Feedback & états | 15 | Tous couverts (loading/success/error/empty) = 15 |
| A11y & mobile | 15 | Contraste + focus + touch OK = 15 |
| Affordances | 10 | Clair = 10, ambigu = 3 |
| Trust signals | 10 | Crédible et placé = 10, absent ou générique = 3 |

Plancher 0, plafond 100.

### 5. Production du rapport

Utilise [templates/review-report.md](../templates/review-report.md).

Structure en 3 bandes **obligatoires** :

- 🔴 **Bloquant** — casse la tâche utilisateur, a11y cassée, confusion majeure, CTA introuvable
- 🟡 **Friction** — ralentit, frustre, mais l'utilisateur arrive au bout
- 🟢 **Polish** — micro-améliorations, hiérarchie fine, transitions

Pour chaque item :
- **Le problème** (1 phrase)
- **Où** (fichier:ligne, ou description précise)
- **Pourquoi** c'est un problème (heuristique violée + impact utilisateur estimé)
- **La correction proposée** (avant / après)
- **Effort** : XS (15min), S (1h), M (demi-journée), L (journée), XL (plusieurs jours)

## Règles d'output

1. **Cite tes frameworks.** « Nielsen #1 », « Hick's law », « Fogg B=MAT » — chaque flag a sa référence. Sinon c'est une opinion.
2. **Impact > esthétique.** « Ce CTA perd ~30% de clics car l'affordance manque » bat « ce CTA est moche ».
3. **Conclusion obligatoire.** Termine par « Ce que je ferais cette semaine » : 3 items MAX.
4. **Chiffres concrets.** « 3 CTAs au-dessus du fold » bat « trop de CTAs ».
5. **Pas de verdict brutal.** Tu rends service à un designer/dev — pas un tribunal. Mais ne sucre pas non plus.

## Exemple d'invocation (auto-trigger)

L'utilisateur dit :
- « Review UX de ma page d'accueil »
- « C'est quoi les problèmes UX sur ce component ? »
- « Est-ce que mon onboarding est bon ? »
- « Feedback design sur cette landing »

→ Lance `/ux review` sur la cible identifiée.

## Ce qu'il NE faut PAS faire

- ❌ Review sans lire le fichier (ou sans voir le screenshot)
- ❌ Confondre avec `/ds audit` — ici c'est l'expérience, pas la cohérence système
- ❌ Rapport de 2000 mots — synthétise, priorise
- ❌ Flagger comme bloquant ce qui est en vrai du polish
- ❌ Inventer des métriques chiffrées sans source (« perd 30% » → dis « probablement 20-30% basé sur études Baymard » si tu cites, sinon reste qualitatif)
- ❌ Corriger le code toi-même — tu audites, l'user implémente
