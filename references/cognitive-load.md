# Cognitive Load — Les règles mentales qui font ou cassent ton UX

> L'utilisateur a un cerveau limité, distrait, pressé. Chaque élément d'interface taxe sa mémoire de travail. Voici comment ça se mesure et comment ça se réduit.

Utilisé par `/ux review` et `/ux improve` pour diagnostiquer la surcharge cognitive et proposer des réductions factuelles.

## Les 4 lois à connaître

### 1. Miller's Law (1956) — 7 ± 2
**Théorie** : La mémoire de travail humaine peut retenir environ **7 éléments** (entre 5 et 9). Au-delà, overload.

**Applications UX** :
- Menu de navigation : **5-7 items max** au top level
- Steps dans un flow multi-étapes : **max 5-7 steps**, sinon fragmenter en sections
- Champs d'un form par écran : **max 5-7 champs**, au-delà multi-step
- Tableau de bord : **5-7 metrics principales** au-dessus du fold, le reste en drill-down

**Nuance moderne** : plutôt **4 ± 1** d'après les études récentes (Cowan 2001). Quand tu peux, vise 3-5.

**Red flag** : navigation avec 12 items au top niveau. L'utilisateur ne scanne pas, il abandonne.

**Fix** : regroupement sémantique (chunking) — 2 « méta-items » qui contiennent chacun 5 sous-items = perception plus légère.

---

### 2. Hick's Law (1952) — Le temps de décision croît logarithmiquement avec le nombre de choix

**Formule** : RT = a + b × log₂(n+1) — où n = nombre de choix.

**Implication pratique** : chaque option ajoutée ralentit la décision. Pas linéairement, mais clairement.

**Applications UX** :
- Pricing : 3 plans beats 5 plans. 5 beats 10.
- CTAs concurrents sur une page : chaque CTA additionnel dilue tous les autres.
- Dropdown long : au-delà de 15 items, utiliser combobox + search.
- Menu de filtres : chunking par catégorie > liste plate de 30 filtres.

**Red flag** : 5 CTAs primaires "également importants" → aucun n'est primaire en pratique.

**Fix** :
- Prioriser UN CTA principal, reléguer les autres en secondaires visuellement.
- Défault intelligent (pré-sélection de l'option la plus probable).
- Progressive disclosure (montrer 3 options, "plus d'options" en clic).

---

### 3. Fogg Behavior Model (2007) — B = MAT

**Théorie** : Le comportement (B) se produit quand **Motivation** (M), **Ability** (A) et **Trigger** (T) convergent au même moment.

- **M (Motivation)** : à quel point l'utilisateur **veut** faire l'action
- **A (Ability)** : à quel point c'est **facile** de la faire
- **T (Trigger)** : est-ce qu'il y a un **appel** à le faire maintenant

**Implication** :
- Si M est bas → augmenter A ou augmenter T (rappel, notification)
- Si A est bas → simplifier, réduire le nombre d'étapes, pré-remplir
- Si T manque → CTA bien placé et motivant

**Applications UX** :
- Onboarding : baisser A au max (autofill, social auth, skip optional)
- Paywall : T au bon moment (après une action de valeur, pas dès l'arrivée)
- Conversion : pré-remplir tout ce qu'on peut (email connu, country-detection)

**Red flag** : form de signup avec 10 champs dès l'atterrissage = A trop bas + M moyenne + T absente = échec.

**Fix** :
- Social auth (Google/GitHub) = A quasi-nul
- Email + password seul pour démarrer, le reste plus tard (delayed profile)
- Captures contextuelles (demander l'info au moment où elle sert)

---

### 4. Jakob's Law (2000)
**Théorie** : Les utilisateurs passent la majorité de leur temps sur d'**autres sites**. Ils s'attendent à ce que ton site fonctionne comme ceux-là.

**Implication** :
- N'invente pas de pattern quand un standard existe
- Les conventions ne sont pas négociables : logo en haut gauche, panier en haut droite, burger sur mobile

**Applications UX** :
- E-commerce : Amazon est le benchmark, que tu le veuilles ou non
- SaaS B2B : les patterns Linear, Notion, Stripe ont créé des attentes
- Forms : les conventions HTML natives (input types, labels) sont optimales — on ne réinvente pas

**Red flag** : design « unique » pour se différencier → utilisateurs désorientés.

**Fix** : innover **sur le contenu**, **pas sur les patterns**. Ton brand peut être unique, ta navigation doit être familière.

## 5 patterns de réduction de charge

### A. Progressive disclosure
Montrer le minimum. Cacher le reste derrière « Advanced options » / « More ».

Exemple : un form simple avec 3 champs visibles, un bouton « Plus d'options » qui révèle 5 champs additionnels seulement si l'utilisateur en a besoin.

### B. Chunking
Grouper les infos en unités sémantiques. Un numéro de carte en `1234 5678 9012 3456` > `1234567890123456`.

Exemple sur form : grouper par sections ("Compte", "Entreprise", "Paiement") avec séparation visuelle.

### C. Defaults intelligents
Pré-remplir ce qui est probable. Pays détecté par IP. Format phone selon locale. Unité de mesure par locale.

Exemple : « monthly » sélectionné par défaut sur un pricing toggle — c'est le choix le plus fréquent.

### D. Context compression
Ne réaffiche pas l'info qui vient d'être saisie — la résume ou la confirme visuellement.

Exemple : après step 1 du checkout, afficher juste « Chérif → Abidjan CI » au lieu de réafficher nom complet + adresse + téléphone.

### E. Recognition over recall (revoir Nielsen #6)
Suggestions, autocomplete, historique récent, favoris. L'utilisateur ne doit pas **se souvenir**, il doit **reconnaître**.

Exemple : dropdown pays avec recherche + "Countries you've used before" en haut.

## Comment mesurer la charge

### Test de lecture : 5-second test
Montre l'écran 5s, cache-le, demande : « Qu'as-tu vu ? À quoi sert cette page ? »
- Mémoire solide → clarté OK
- Confusion → overload

### Test de task : first-click test
« Tu veux faire X, clique où tu penses. » Pas de reflexion longue = interface lisible.

### Métrique proxy
Time-to-first-action sur un signup > 30s = friction excessive. Sur un dashboard > 10s = hiérarchie floue.

## Checklist anti-surcharge

Avant de livrer un écran :

- [ ] Combien d'éléments visuels distincts ? Si > 7 au-dessus du fold, simplifier.
- [ ] Combien de CTAs ? Un seul primaire, les autres secondaires.
- [ ] Combien d'icônes ? Si sans texte, sont-elles universelles ou customs ?
- [ ] Combien de couleurs accent ? 1-2 max. Si chaque item a sa couleur, rien ne ressort.
- [ ] Combien de niveaux de navigation ? 2 max (top + sidebar). 3 = perdu.
- [ ] Est-ce que j'ai mis des defaults ? Pré-sélection quand possible.
- [ ] Est-ce que j'ai chunk-é ? Sections, séparateurs, groupes.
- [ ] Le mobile passe-t-il ? (taille touch, thumb zone, texte lisible)

## Ressources

- George Miller (1956), *The Magical Number Seven, Plus or Minus Two*
- W.E. Hick (1952), *On the rate of gain of information*
- BJ Fogg (2007), *Tiny Habits*
- Jakob Nielsen (2000), *Jakob's Law*
- Steven Krug, *Don't Make Me Think*
