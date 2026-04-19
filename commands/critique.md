# `/ux critique [target]` — Feedback senior focus

> Un avis court, direct, d'un senior qui a vu passer 500 écrans.

## Objectif

Quand l'utilisateur veut un retour rapide sans le formalisme d'un audit complet. **5 observations max**, pas plus. L'équivalent de « hey, t'as 2 minutes, tu peux regarder ? » dans un Slack avec un senior designer.

## Input

- Un fichier de composant
- Une page
- Un screenshot
- Une description verbale (« ma pricing page »)

## Process

### 1. Rapide contexte

Pas besoin du processus formel de `/ux review`. Mais **quand même** :
- Lire le fichier (si code) — pas juste deviner
- Identifier le type d'écran en 1 phrase dans ta tête
- Comprendre le goal principal

### 2. Sortie structurée : 5 observations max

**2 choses qui marchent vraiment** (genuine, pas de flatterie)
**3 choses qui font mal** (specific, actionable)

Pour chaque observation :
- **1 phrase punchy** — pas de préambule
- **Référence à une heuristique** (Nielsen #X, Hick, Fogg, Gestalt…)
- **Impact concret** (« perd des clics », « crée du doute », « ralentit la complétion »)
- **Ce que tu ferais à la place** — si applicable, une phrase max

### 3. Ton & style

- **Direct, pas brutal.** Tu rends service.
- **Zéro bullshit.** Pas de « super travail ! » pour adoucir.
- **Un senior qui a déjà vu ça.** Tu reconnais les patterns rapides.
- **Langue** : FR pour la prose, EN pour le tech.
- **Emoji utile** : ✅ pour ce qui marche, 🚨 pour ce qui casse, 💡 pour le fix suggéré.

### 4. Format de sortie

Utilise [templates/critique-report.md](../templates/critique-report.md).

Rester **sous 400 mots total**. Si tu as plus à dire → propose `/ux review` pour le complet.

## Exemple de sortie

```markdown
## Critique — Hero de la page Pricing

**Type** : landing/pricing page

### ✅ Ce qui marche
- **Prix affiché gros, une seule fois.** Zéro ambiguïté sur le coût,
  ce qui élimine le doute #1 d'un achat en ligne (Baymard).
- **Testimonial placé AVANT le CTA.** Bon call — la preuve sociale
  réduit le risque perçu juste avant l'engagement (Cialdini).

### 🚨 Ce qui fait mal

1. **3 CTAs primaires au-dessus du fold.**
   "Start free", "Book demo", "Contact sales" rivalisent pour
   l'attention. Hick's law : le temps de décision explose. **Fix** :
   garde UN CTA primaire (le plus probable), reléguer les 2 autres
   en secondaires stylistiquement.

2. **H1 = feature, pas bénéfice.**
   "Plans flexibles pour tous les usages" : tu dis QUOI tu vends,
   pas POURQUOI. **Fix** : "Lance ton SaaS sans t'endetter" ou
   équivalent bénéfice-orienté. Kahneman : le bénéfice bat la feature
   à chaque fois.

3. **Aucun empty state pour users anonymes sur le trial.**
   Après sign-up, ils voient un dashboard vide sans guidance. Fogg
   B=MAT : trigger absent au moment de la plus haute motivation.
   **Fix** : onboarding 3-step avec use case concret.

---

Plus de temps ? Lance `/ux review` pour l'audit complet.
```

## Règles

1. **Strict 5 observations max.** Si tu en as 10, fais `/ux review`, pas `critique`.
2. **Equilibre 2/3.** Toujours 2 positives + 3 négatives. Ça ancre la crédibilité.
3. **Cite les frameworks.** Sinon c'est une opinion.
4. **Phrase courte.** Un senior est économe de mots.
5. **Pas de template rigide.** C'est un feedback, pas un formulaire.

## Quand l'utiliser vs `/ux review`

| | `critique` | `review` |
|---|---|---|
| Scope | Un écran, vite fait | Un écran ou un flow, en profondeur |
| Taille output | < 400 mots | 1000-2000 mots |
| Score | Non | Oui, /100 |
| Plan d'action | Non, juste les observations | Oui, priorisé |
| Quand | « J'ai 2 min, regarde ça » | « Je veux un plan pour améliorer » |

## Ce qu'il NE faut PAS faire

- ❌ Écrire un rapport long — c'est le rôle de `/ux review`
- ❌ Flatter pour adoucir
- ❌ Être brutal sans solution proposée
- ❌ Invoquer 10 principes — 1-2 bien choisis par observation suffisent
- ❌ Traiter tous les aspects — focus sur les signaux les plus forts
