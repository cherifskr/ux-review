# UX Patterns — Ce qui marche et ce qui casse

> Bibliothèque de patterns (bons et anti-patterns) que `/ux review` et `/ux improve` mobilisent. Structurée par contexte d'usage.

Ce n'est pas exhaustif — c'est les patterns qu'on rencontre le plus souvent dans un audit.

## 🌐 Landing pages

### ✅ Bons patterns

**Hero en 3 couches**
1. H1 bénéfice (« Lance ton SaaS en 48h »)
2. Sub-title contexte (« Template Next.js + Stripe + Auth, prêt à déployer »)
3. CTA primaire unique (« Commencer gratuitement »)

**Social proof before conversion**
Logos de clients, testimonials, ou metric (« 5k+ devs l'utilisent ») placés **juste avant** ou **à côté** du CTA. Réduit le risque perçu au moment où il compte.

**Asymmetric CTA hierarchy**
1 CTA primaire (bouton plein, couleur accent), 1 CTA secondaire (outline ou lien discret) max. Jamais 3 primaires.

**Problem/Solution framing**
Tu identifies la douleur avant de vendre la solution. « Marre de refaire la même landing 10 fois ? » → « Avec ce template… »

### 🚫 Anti-patterns

- **Navigation pleine sur landing pure** : nav complète = autant de distractions qui te sortent du CTA. Sur landing conversion, minimaliste (logo + 1 CTA nav).
- **Too many CTAs above the fold** : « Get started », « Book demo », « Contact sales », « Watch video » — aucun ne gagne.
- **Hero vague** : « The platform for modern teams » — ça peut dire tout et rien. Sois spécifique.
- **Testimonials génériques** : pas de photo, pas de nom complet, citation vague. Pire que pas de testimonial.
- **Cookie banner qui bouffe le hero** : a11y required, mais design-le pour ne pas masquer le CTA primaire sur mobile.

## 📝 Forms

### ✅ Bons patterns

**Labels au-dessus**
Pas placeholder-only. Le placeholder disparaît quand on tape, et on oublie ce qu'on devait mettre. Label **au-dessus**, toujours visible.

**Validation inline on blur**
Dès que l'utilisateur quitte un champ, tu valides et tu feedback. Pas de « submit → 7 erreurs d'un coup ».

**Required marqué**
Astérisque rouge **ET** `aria-required="true"`. Ne fait pas l'inverse (marquer les optionnels) — contrairement au conseil de certains, c'est plus long cognitivement.

**Helper text pertinent**
Sous le champ : « Le mot de passe doit contenir 8 caractères minimum » affiché **avant** la saisie, pas après l'erreur.

**Autocomplete HTML**
`autocomplete="email"`, `autocomplete="name"`, `autocomplete="tel"` — magie gratuite sur mobile.

**Multi-step pour forms longs**
> 7 champs → split en 2-3 étapes. Exploite le sunk cost effect.

### 🚫 Anti-patterns

- **Placeholder comme label** : classique tueur de conversion. L'utilisateur oublie ce que demandait le champ dès qu'il commence à taper.
- **Erreurs en haut du form** : « 5 erreurs trouvées » avec liste — quel champ exactement ? Résumé accepté SI il links vers les champs concernés.
- **Champ tél sans format** : « 0641234567 », « +33 6 41 23 45 67 », « 06-41-23-45-67 » — pourquoi pas un mask ?
- **Captcha agressif** : reCAPTCHA v3 invisible > v2 "pick all traffic lights". Drop-off énorme sur v2.
- **Confirmation email obligatoire avant accès au produit** : friction énorme. Laisse accéder en mode preview, confirme plus tard.
- **« Create password » sans hint en temps réel** : barre de force qui update dynamique, mieux que « weak » après submit.

## 🧭 Navigation

### ✅ Bons patterns

**2 niveaux max**
Top nav (5-7 items) + éventuellement sidebar (sections de l'item actif). Pas de mega-menu à 4 niveaux.

**Persistent primary nav**
Sticky top sur desktop, bottom tabs sur mobile (thumb zone). Garder l'orientation.

**Command palette (cmd+K)**
Sur les outils denses (admin, docs), une palette avec search > mega-menu fouillé.

**Breadcrumbs pour deep content**
Docs, catalogues produits, admin avec N sections : breadcrumbs visibles en haut.

### 🚫 Anti-patterns

- **Hamburger sur desktop** : cache la nav pour rien. Garde la nav visible dans un espace spacieux.
- **Mega-menu au hover** : s'ouvre par accident, reste ouvert trop longtemps. Si mega-menu, clic only.
- **Bottom nav 5+ items sur mobile** : au-delà de 4-5, les items sont trop petits pour le pouce.
- **Nav qui disparaît au scroll et ne revient jamais** : UX mobile typique qui frustre quand on veut naviguer en plein scroll.

## 📊 Dashboards

### ✅ Bons patterns

**Priority-first layout**
Les 3-5 metrics principales **au-dessus du fold**, grandes et claires. Le reste en drill-down.

**Trend at a glance**
Sparkline ou arrow + percentage à côté de la value (« $45k ↗ +12% vs last week »).

**Actionable empty state**
Pas de « No data yet » vide. « Ajoute ta première intégration pour voir les metrics » + bouton.

**Drill-down par clic**
Clic sur une metric → modal ou page avec le détail, le graph temporel, les outliers.

**Refresh visible**
Timestamp « Updated 2 min ago » + bouton refresh manuel. Pas de black box.

### 🚫 Anti-patterns

- **Density uniforme** : tout pareil, rien ne ressort. Hiérarchie obligatoire.
- **Metrics sans contexte** : « 147 users » vs « 147 users (+12%) ». Sans trend, la valeur n'a pas de sens.
- **Charts décoratifs** : graph qui ne raconte rien, ajouté « because dashboard ».
- **Filtres cachés** : « Advanced filters » qui ouvre une modale. Les filtres sont l'interaction principale, rends-les visibles.
- **Date picker qui défaut 30 jours** sans le dire : l'utilisateur croit voir all-time, conclut faux.

## 🗃️ Listings

### ✅ Bons patterns

**Skeleton during load**
> 300ms de chargement → skeleton qui matche la future structure. Perçu 2x plus rapide qu'un spinner.

**Actionable empty state**
3 layers : icône friendly, message encourageant, CTA pour démarrer. Pas « No items found ».

**Bulk actions visibles quand selection**
Checkbox row → toolbar flottante apparaît avec les actions (delete, export, tag).

**Infinite scroll avec indicator**
Si infinite, montre « Loading more… » pas juste sudden append. Et garde un footer accessible (impossible avec infinite — ajoute un bouton « Back to top »).

### 🚫 Anti-patterns

- **Pagination mal placée** : en bas seulement, sur une listing de 100 rows, l'utilisateur scroll et se perd.
- **Empty state décourageant** : « No results. Try different keywords » sans suggestion ni call to action.
- **Loading sur toute la page pour filter change** : préfère swap du contenu seulement, garde la nav/filter sticky.
- **Pas de skeleton + page blanche** : utilisateur ne sait pas si ça charge ou si c'est vide.

## 🚪 Onboarding

### ✅ Bons patterns

**Progressive onboarding**
Pas tout d'un coup. Révèle les features **au moment où elles deviennent utiles**. Tooltip contextuel > grand tour initial.

**Value first, setup later**
L'utilisateur doit toucher à de la valeur **avant** de remplir son profile complet. Slack le fait : envoyer un message avant de customiser l'avatar.

**Checkpoints clairs**
Liste des 3-5 étapes avec check progressif. L'utilisateur voit ce qui reste à faire.

**Escape hatches**
« Skip » visible à chaque étape. Forcer l'onboarding = drop-off.

**Empty states pédagogiques**
Dashboard vide juste après signup → message + screenshot + « Start first task » button.

### 🚫 Anti-patterns

- **Modal obligatoire avec 10 champs à remplir avant d'accéder** : drop-off massif. Capture progressive.
- **Tour guidé de 12 steps** : nobody reads them all. Fais 3-4 steps max et contextuel.
- **Demander accès aux notifs/location dès le premier écran** : NON. Demande au moment où l'info sert (permission request in context).
- **« Choose a plan » avant d'utiliser le produit** : le user ne sait pas ce qu'il choisit. Trial first, paywall after.

## 💳 Checkout / Conversion

### ✅ Bons patterns

**Guest checkout**
Forcer la création de compte avant d'acheter → abandon. Guest checkout par défaut, option « save for next time » après.

**Progress visible**
« Shipping → Payment → Review → Confirmation » toujours visible.

**Summary persistent**
Le cart résumé reste visible (sticky desktop, expandable mobile) pendant tout le checkout.

**Price transparence totale**
Tous les frais visibles **dès** le cart — pas de surprise au step payment. Source #1 de drop-off e-commerce (Baymard).

**Trust signals au moment de payer**
Logos de cartes acceptées, badge SSL, « Secure checkout », logos partenaires paiement. Réduit l'anxiété.

**Multi-payment options**
Card, Apple Pay, Google Pay, PayPal — plus de choix = moins de friction (mais pas Hick's law inversé : ces options sont connues, pas comparées).

### 🚫 Anti-patterns

- **Surprise fees at payment step** : frais de livraison révélés à la dernière seconde = abandon massif.
- **Create account required** : -35% conversion en moyenne vs guest (Baymard).
- **Pas de validation de card en temps réel** : user saisit les 16 chiffres, clique, boom erreur. Validation inline.
- **Confirmation email seulement, pas de page success** : « did the payment work? » anxiété.

## 🚨 Errors / Edge cases

### ✅ Bons patterns

**Error pages human**
404 avec illustration + « Let's get you back » + lien home + search. Pas juste "404 Not Found".

**Inline errors proches du champ**
Champ invalid → message **sous le champ concerné**, rouge + icône.

**Toast pour errors non-field**
Network error, timeout, server error → toast persistant avec action « Retry ».

**Offline support**
Service worker détecte offline, montre un banner « You're offline — some features may not work ». Bonus : cache les pages visitées.

### 🚫 Anti-patterns

- **Toast qui disparaît après 3s avec une erreur critique** : l'utilisateur n'a pas eu le temps de lire. Errors = persistent + dismiss manuel.
- **Error message technique** : « InternalServerException: NullPointer at line 42 » — traduisible, stp.
- **Pas de recovery path** : error dead-end sans back/retry/home. Chaque erreur a 3 issues minimum.
- **Banner sticky permanent qui devient du bruit** : les users ignorent vite le « Cookie consent » qui ne disparaît pas.

## 🌙 Dark mode / Theming

### ✅ Bons patterns

**System preference default**
`prefers-color-scheme` respecté au premier load. L'user peut override.

**Toggle visible**
Bouton accessible, dans la nav ou les settings.

**Contraste préservé**
Dark mode ≠ inverser les couleurs. Review a11y indépendamment pour chaque theme.

**Images adaptées**
Logos avec variante dark, illustrations qui ne deviennent pas invisibles sur fond noir.

### 🚫 Anti-patterns

- **Toggle caché en settings** : si tu offres dark mode, rends-le trouvable.
- **Forcer dark ou light** : laisse l'user choisir, respect system default.
- **Couleurs sursaturées en dark** : un rouge pur (#FF0000) sur noir fait mal aux yeux. Désature légèrement.

## 📚 Ressources

- [Baymard Institute](https://baymard.com/) — E-commerce UX benchmarks
- [Nielsen Norman Group](https://www.nngroup.com/) — research-backed UX articles
- [Growth.Design](https://growth.design/) — case studies UX/growth
- [Refactoring UI](https://refactoringui.com/) — Adam Wathan, Steve Schoger
- Don Norman, *The Design of Everyday Things*
- Kathy Sierra, *Badass: Making Users Awesome*
