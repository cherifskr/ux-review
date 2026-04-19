# `/ux improve [target]` — Propositions d'amélioration raisonnées

> Ne pointe pas juste ce qui cloche — propose **comment** le fixer, avec tradeoffs.

## Objectif

Quand l'utilisateur a déjà identifié une problématique UX et veut des propositions concrètes d'amélioration. Pas un audit (trop large), pas un feedback (trop court) — **une proposition raisonnée avec 2-3 options et une reco**.

## Input

- Un fichier/écran + une question (« comment améliorer la conversion ? »)
- Une description de flow + un goal (« rendre l'onboarding moins long »)
- Un screenshot + un pain point (« les users abandonnent ici »)

## Process

### 1. Comprendre le problème à résoudre

Si l'utilisateur n'a pas précisé le goal, **demande-le avant de coder**. Pas de propositions sans problème clair :
- Quel est le symptôme observé ? (taux de drop-off, clics ratés, confusion feedback…)
- Quelle metric tu veux bouger ? (conversion, time-to-task, errors…)
- Quelles contraintes ? (ne peut pas refaire de zéro, pas de backend change, etc.)

### 2. Cadrer 2-3 options

Présente **2 ou 3 options** (pas plus), chacune avec :

- **Nom de l'approche** (court, mémorable — « Disclosure progressif », « One-page refactor », « Multi-step form »…)
- **Ce que tu changes concrètement** (pas abstrait, décris l'écran résultat)
- **Pros** : ce que l'option apporte (métrique impactée, effort cognitif réduit, etc.)
- **Cons** : ce qu'elle coûte (dev effort, complexité, risque)
- **Ça gagne quand** : le contexte où cette option est la meilleure

### 3. Annoncer ta reco

Termine par **une recommandation explicite**. Pas « les 3 options sont valables, à toi de voir » — un senior a une préférence argumentée :

> « Je prendrais l'Option B parce que [contexte] et [contrainte] font que [raison principale]. L'option A marcherait aussi, mais [limite]. »

### 4. Détails de l'option recommandée

Pour l'option choisie seulement, précise :
- **Éléments UI impactés** (liste des composants modifiés)
- **Hiérarchie post-change** (H1 → sous-texte → CTA → social proof)
- **Heuristiques respectées** (Nielsen #X, Hick's law…)
- **Métriques attendues** (si possible, citer des benchmarks : Baymard, NNGroup, UX Stars)
- **Questions ouvertes** — ce que tu n'as pas tranché, qui nécessite validation équipe/data

### 5. Ce que tu NE dois PAS faire

Tu **n'écris pas** le code final. Cette commande produit une **spec** d'amélioration, pas une implémentation. Si l'utilisateur valide, il peut te demander d'implémenter ensuite (phase séparée).

## Exemple de sortie

```markdown
## /ux improve — Réduire le drop-off sur le form de signup

**Problème identifié** : 48% des visiteurs abandonnent au 3e champ du form (d'après la question posée). Goal : remonter la completion rate > 70%.

### Option A — Single-page form (statu quo, nettoyé)

**Ce qu'on change** : Tous les 8 champs restent sur une page, mais :
- Labels au-dessus (pas placeholder-only)
- Validation inline dès blur
- Required markés visuellement + "optional" sur les autres
- Champs "nice to have" retirés (bio, company size)

**Pros** : Minimal effort dev, pas de dépendance routing, users voient l'ensemble immédiatement.
**Cons** : Reste visuellement intimidant. Probablement +5-10% completion, pas +20%.
**Gagne quand** : pas de temps dev, on est déjà proche du goal.

### Option B — Multi-step avec progress

**Ce qu'on change** : Split en 3 étapes de 2-3 champs :
1. Essentiel (email + password)
2. Identité (prénom + company)
3. Contexte (use case — optionnel)

Progress bar en haut, bouton "Back" toujours visible.

**Pros** : Effet "foot in the door" (Cialdini) — une fois step 1 passé, abandon baisse drastiquement. Baymard : +13% en moyenne sur flows similaires.
**Cons** : Code plus complexe (routing, state persistence), 2x plus d'écrans à designer.
**Gagne quand** : les champs sont vraiment nécessaires et qu'on peut prioriser l'essentiel.

### Option C — Social auth first + profile plus tard

**Ce qu'on change** : Gros bouton "Sign up with Google/GitHub" en primaire, email/password en secondaire. Pas de profile complet au signup — on capture les infos manquantes quand elles deviennent utiles.

**Pros** : Friction minimale (1 clic vs 8 champs), +40-60% completion selon études Baymard.
**Cons** : Demande un backend OAuth, nécessite un delayed profile completion, peut paraître "cheap" pour un SaaS B2B premium.
**Gagne quand** : audience grand public ou dev, et tu as le dev pour OAuth.

---

### 💡 Ma reco

**Option B — Multi-step avec progress.**

Pourquoi : ton form a 8 champs vraiment nécessaires (d'après le contexte), donc C n'est pas viable. A apporterait un gain marginal. B exploite le biais psychologique "sunk cost" qui fait que les users continuent une fois qu'ils ont investi du temps sur step 1.

### Détails de l'implémentation

**UI impactée** :
- `<SignupForm>` → split en `<SignupStep1>`, `<Step2>`, `<Step3>`
- Nouveau composant `<ProgressBar>` en haut
- Persistance state : useReducer ou React Hook Form context
- Bouton "Back" toujours accessible + "Save and finish later" sur step 3

**Hiérarchie nouvelle** :
- Progress bar (subtil)
- H1 : "Crée ton compte" (step 1) → "On te connaît un peu mieux" (step 2) → "Dernière étape" (step 3)
- Champs (2-3 max)
- CTA primaire "Continuer" → "Terminer" en step 3
- Lien secondaire "Retour" (discret)

**Heuristiques respectées** :
- Nielsen #1 (visibility of status) : progress bar
- Nielsen #3 (user control) : back button toujours présent
- Cialdini (commitment) : effet foot-in-the-door
- Fogg B=MAT : ability augmentée car task chunking

**Métriques attendues** (sources : Baymard, NNG)
- Completion rate : +10-20% (de 52% à ~65-70%)
- Drop-off shift : moins de drops au step 2-3 qu'au step 1
- Time-to-complete : similaire total, mais perçu plus court

**Questions ouvertes**
- [ ] Quel state management utiliser ? (Context vs URL params pour deep-linking)
- [ ] Permettre la navigation libre entre steps ou séquentiel ?
- [ ] Save-as-draft entre sessions ?
```

## Règles d'output

1. **Jamais moins de 2 options, jamais plus de 3.** En dessous, c'est un diktat. Au-dessus, l'utilisateur a trop à comparer (Hick's law appliquée à la review elle-même).
2. **Toujours annoncer ta reco.** Un senior a un avis, le partage, argumente. Pas de « à toi de voir ».
3. **Tradeoffs honnêtes.** Si l'option reco a un inconvénient, dis-le. Pas de sales pitch.
4. **Citer des benchmarks quand possible.** Baymard, NNGroup, UX Stars, Growth studies. Sinon qualifie (« probablement », « dans les cas similaires »).
5. **Spec, pas code.** La sortie est un plan d'action — l'utilisateur valide avant d'implémenter.

## Quand l'utiliser

| | `/ux improve` | `/ux review` | `/ux critique` |
|---|---|---|---|
| L'utilisateur sait déjà | Oui (a identifié le problème) | Non (veut un diagnostic) | Non (veut un avis) |
| Output | Propositions ciblées | Audit complet + plan | 5 observations flash |
| Taille | ~800-1200 mots | 1500-2500 mots | < 400 mots |

## Ce qu'il NE faut PAS faire

- ❌ Commencer sans avoir le goal/problème clair
- ❌ Proposer 1 seule option (diktat) ou 5+ (paralysie)
- ❌ Recommandation molle (« les 3 sont valables »)
- ❌ Écrire le code final — la spec suffit
- ❌ Inventer des métriques sans source
