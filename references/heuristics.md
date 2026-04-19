# Usability Heuristics — Nielsen 10 revisitées pour 2026

> Les 10 règles de Jakob Nielsen (1994) ont 30 ans. Elles tiennent toujours. Voici comment les appliquer à des interfaces modernes web/mobile.

Utilisé par `/ux review` pour flagger chaque problème avec sa règle violée. Utilisé par `/ux critique` comme vocabulaire de feedback.

## Les 10 heuristiques (version 2026)

### 1. Visibility of system status
**Règle** : L'interface doit toujours informer l'utilisateur de ce qui se passe, avec un feedback approprié dans un temps raisonnable.

**Applications modernes** :
- ✅ Loading state visible (skeleton > spinner > rien)
- ✅ Success toast après une action
- ✅ Progress bar pour les uploads / multi-step forms
- ✅ État "enregistré" vs "modifié" sur les forms
- ❌ Click sans feedback = utilisateur reclique = double-post

**Red flags** :
- Action qui dure > 1s sans loading state
- Form submit sans indication success
- Connexion/déconnexion sans toast

---

### 2. Match between system and real world
**Règle** : Parler la langue de l'utilisateur, pas la langue du code.

**Applications modernes** :
- ✅ « Supprimer » et pas « Delete record »
- ✅ « Votre panier est vide » et pas « 0 items in cart »
- ✅ Icons universellement comprises (home, cart, search)
- ❌ Jargon interne exposé (« Node 404 », « Payload invalid »)

**Red flags** :
- Codes d'erreur bruts (HTTP 500 affiché à l'utilisateur)
- Terminologie développeur (« param », « payload », « request »)
- Structures type « FirstName » affichés avec underscores

---

### 3. User control and freedom
**Règle** : L'utilisateur doit pouvoir revenir en arrière, annuler, quitter.

**Applications modernes** :
- ✅ Undo après action destructive (toast avec "Undo" 5s)
- ✅ Breadcrumbs pour flows profonds
- ✅ Escape/Click outside ferme les modals
- ✅ Confirmation avant action destructive
- ❌ Modal sans bouton fermer
- ❌ Action sans undo + sans confirmation

**Red flags** :
- Delete sans confirmation ni undo
- Flow multi-step sans bouton back
- Modal qui bloque (pas d'escape, pas de close)

---

### 4. Consistency and standards
**Règle** : Suivre les conventions de la plateforme. Mêmes mots pour mêmes actions. Même design pour mêmes composants.

**Applications modernes** :
- ✅ "Annuler" à gauche, "Confirmer" à droite (convention Western)
- ✅ Bouton primaire = toujours même couleur, même placement
- ✅ Navigation patterns platform-native (sidebar sur desktop, bottom tabs sur mobile)
- ❌ Deux mots différents pour la même action dans l'app (« Modifier » ici, « Éditer » là)
- ❌ Design custom qui casse les patterns reconnus

**Red flags** :
- Icônes ambiguës (un œil pour "voir" OK, mais un œil barré pour "cacher" peut être pris pour "bloquer")
- Convention inversée : Submit à gauche, Cancel à droite = WTF
- Composants custom réinventés pour le plaisir

---

### 5. Error prevention
**Règle** : Mieux vaut prévenir que guérir. Éliminer les conditions d'erreur ou demander confirmation avant.

**Applications modernes** :
- ✅ Validation inline pendant la frappe (pas juste à submit)
- ✅ Désactiver le submit tant que le form est invalide
- ✅ Format pré-contraint (date picker vs input libre)
- ✅ Champs read-only pour les données non-modifiables
- ❌ Valider en bloc au clic submit seulement
- ❌ Masque de saisie absent (numéros tel, cartes, dates)

**Red flags** :
- Submit qui renvoie en bloc 5 erreurs après avoir rempli 20 champs
- Confirm destructif sans check "I understand"
- Dropdown vide possible avec required=true

---

### 6. Recognition rather than recall
**Règle** : L'utilisateur ne doit pas avoir à mémoriser de l'info d'un écran à l'autre. Rendre tout visible ou facilement accessible.

**Applications modernes** :
- ✅ Breadcrumbs au lieu de « remember where you are »
- ✅ Autocomplete sur les inputs (pas "try to remember the exact name")
- ✅ Recent searches visibles
- ✅ Drafts visibles, pas cachés
- ❌ Instructions en page 1 qu'il faut retenir en page 5
- ❌ Mémoriser un ID pour le retaper plus tard

**Red flags** :
- Form avec référence à une info vue page précédente
- Onboarding avec info donnée et non réaffichée quand nécessaire
- Confirmation email qui ne rappelle pas ce que l'utilisateur a rempli

---

### 7. Flexibility and efficiency of use
**Règle** : Fournir des raccourcis pour les power users sans encombrer les novices.

**Applications modernes** :
- ✅ Shortcuts clavier visibles (cmd+K pour search)
- ✅ Templates, presets, favoris
- ✅ Keyboard navigation complète (arrow keys, Tab, Esc)
- ✅ Personnalisation (dark mode, density, ordre colonnes)
- ❌ Everything same-everything pour tout le monde
- ❌ Pas de shortcut pour les actions fréquentes

**Red flags** :
- Pas de cmd+K / Ctrl+K sur un dashboard complexe
- Pas de "recent" / "favorites" / "bookmarks"
- Expert users forcés de refaire 5 clics à chaque fois

---

### 8. Aesthetic and minimalist design
**Règle** : Chaque unité d'information supplémentaire dilue les autres. Ne montrer que ce qui compte.

**Applications modernes** :
- ✅ Un seul CTA primaire au-dessus du fold
- ✅ Disclosure progressif (advanced options cachées par défaut)
- ✅ Metrics dashboard : priorité visuelle sur les 3-5 plus importantes
- ✅ Hero épuré : 1 headline, 1 sub, 1 CTA, 1 image/video
- ❌ 5 CTAs en compétition pour l'attention
- ❌ Information density uniforme (tout pareil = rien ne ressort)

**Red flags** :
- Plusieurs CTAs primaires sur même écran
- Sidebar + header + toolbar + inline actions = cockpit d'avion
- Texte dense partout, aucune respiration

---

### 9. Help users recognize, diagnose, and recover from errors
**Règle** : Les messages d'erreur doivent être en langage clair, identifier précisément le problème, et suggérer une solution.

**Applications modernes** :
- ✅ Erreur inline à côté du champ problématique
- ✅ Message spécifique : « Email doit contenir @ » et pas « invalid format »
- ✅ Bouton « Try again » ou « Contact support » sur error pages
- ✅ Animation/couleur qui attire l'œil sans être agressive
- ❌ « Error occurred » sans contexte
- ❌ Messages uniquement en rouge sans texte (couleur seule = insuffisant, Nielsen #9 + a11y)

**Red flags** :
- 404 page sans recovery (juste "Page not found")
- Form error générique sans pointer le champ
- Stack trace technique affichée au user

---

### 10. Help and documentation
**Règle** : Idéalement l'interface est self-explanatory. Mais la doc doit exister et être accessible au moment du besoin.

**Applications modernes** :
- ✅ Tooltips contextuels sur les concepts non-évidents
- ✅ Inline hints (« format: DD/MM/YYYY »)
- ✅ Empty states avec lien vers la doc appropriée
- ✅ Command palette avec « Help » intégré
- ❌ FAQ cachée en footer qu'on ne trouve jamais
- ❌ Zero contextual help sur interface complexe

**Red flags** :
- Terme jargon sans tooltip d'explication
- Page d'erreur sans lien support
- Power features non documentées

## Heuristiques additionnelles pour 2026

### 11. Respect the user's time
**Règle** : Le temps utilisateur est la ressource la plus précieuse. Chaque seconde d'attente = drop-off potentiel.

- ✅ Perf < 3s pour First Contentful Paint
- ✅ Skeleton loading (perçu plus rapide que spinner)
- ✅ Optimistic UI (action paraît immédiate, rollback si échec)
- ❌ Page qui clignote pendant le chargement (layout shift)
- ❌ Modal de validation qui prend 2s à s'ouvrir

### 12. Privacy by default
**Règle** : Demander le minimum d'info nécessaire. Expliquer pourquoi quand on demande.

- ✅ Cookie banner avec opt-in, pas opt-out
- ✅ « Pourquoi on demande ton email ? » sous le champ
- ✅ Options de suppression de compte visibles (pas dans dark pattern)
- ❌ Dark patterns (« Yes, I want » bouton vert, « No thanks » texte tiny)
- ❌ Permissions demandées au début sans contexte

### 13. Accessibility IS usability
**Règle** : L'a11y n'est pas une feature séparée, c'est la base. Tout user en bénéficie.

Voir référence dédiée dans `design-system-pro/references/a11y-checklist.md`.

## Checklists par type d'écran

### Landing page
- [ ] Proposition de valeur claire en 5 secondes (H1 + sub) — Nielsen #1
- [ ] **UN** CTA primaire au-dessus du fold — Nielsen #8
- [ ] Social proof (logos, témoignages, metrics) placé avant ou à côté du CTA — Cialdini
- [ ] Hero image/video qui renforce le message (pas juste déco) — Nielsen #2
- [ ] Navigation simplifiée (parfois zéro nav sur landing pure) — Nielsen #8
- [ ] Mobile : thumb zone respectée, CTA à portée de pouce

### Form
- [ ] Label au-dessus du champ (pas placeholder-only) — Nielsen #6
- [ ] Required markés visuellement ET accessiblement — Nielsen #5
- [ ] Validation inline on blur (pas seulement à submit) — Nielsen #5
- [ ] Messages d'erreur à côté du champ, pas en tête — Nielsen #9
- [ ] Autocomplete renseigné (`autocomplete="email"` etc.) — Nielsen #7
- [ ] Format masks pour phone, card, date — Nielsen #5
- [ ] Progress si multi-step — Nielsen #1
- [ ] Save draft ou "resume later" sur form long

### Dashboard
- [ ] Metrics principales **au-dessus** du fold — Nielsen #8
- [ ] Hiérarchie visuelle (tailles, couleurs, groupes Gestalt)
- [ ] Filtres découvrables (pas cachés sous un bouton vague) — Nielsen #6
- [ ] Empty state utile (pas juste "No data")
- [ ] Refresh data manuel ET auto si applicable — Nielsen #3
- [ ] Export / share depuis la vue

### Listing
- [ ] Empty state orienté action (« Add your first X ») — Nielsen #10
- [ ] Skeleton pendant chargement — Nielsen #1
- [ ] Pagination ou infinite scroll cohérents
- [ ] Sort et filters visibles
- [ ] Bulk actions si applicable
- [ ] Scan rapide facile (texte dense = échec)

### Detail
- [ ] Back button ou breadcrumb — Nielsen #3
- [ ] Titre/contexte haut (pas à deviner d'où on vient) — Nielsen #6
- [ ] Primary action visible (edit, delete, share) — Nielsen #8
- [ ] Related content en bas pour re-engagement — Recognition vs recall
- [ ] Share URL qui re-ouvre le même contexte

### Flow multi-étapes (onboarding, checkout)
- [ ] Progress visible (step 2 of 4) — Nielsen #1
- [ ] Back toujours présent — Nielsen #3
- [ ] Save state automatique
- [ ] Résumé de ce qu'on a rempli aux étapes précédentes — Nielsen #6
- [ ] Escape hatch (save for later, cancel) — Nielsen #3

## Ressources

- [Nielsen Norman Group — 10 Usability Heuristics](https://www.nngroup.com/articles/ten-usability-heuristics/)
- [Baymard Institute — E-commerce UX benchmarks](https://baymard.com/)
- Don Norman, *The Design of Everyday Things*
- Steve Krug, *Don't Make Me Think*
