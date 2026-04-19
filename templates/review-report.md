# UX Review — {{screen-or-page-name}}

> Scanné le {{date}} via `/ux review`
> Cible : `{{target-path}}` · type d'écran : **{{screen-type}}**

## Score global : **{{score}} / 100**

{{score-interpretation}}
*(90+ : excellent · 70-89 : solide, quelques poches de friction · 50-69 : friction installée, action nécessaire · < 50 : refonte structurelle à prévoir)*

---

## 📊 Synthèse en une page

| Axe | État | Score |
|---|---|---|
| **Clarté de proposition** | {{clarity-status}} | {{clarity-score}} / 20 |
| **Hiérarchie visuelle** | {{hierarchy-status}} | {{hierarchy-score}} / 15 |
| **Friction cognitive** | {{friction-status}} | {{friction-score}} / 15 |
| **Feedback & états** | {{feedback-status}} | {{feedback-score}} / 15 |
| **A11y & mobile** | {{a11y-status}} | {{a11y-score}} / 15 |
| **Affordances** | {{afford-status}} | {{afford-score}} / 10 |
| **Trust signals** | {{trust-status}} | {{trust-score}} / 10 |

---

## 🔴 Bloquant — {{blocking-count}} item(s)

*Casse la tâche utilisateur. À fixer avant toute autre chose.*

### 🔴 1. {{title}}

**Règle violée** : {{nielsen-or-framework-reference}}

**Où** : `{{file-path-and-line}}` *(ou description précise)*

**Le problème** : {{one-sentence-problem-statement}}

**Impact utilisateur** : {{concrete-user-impact}} *(ex: "perd ~30% de clics car l'affordance manque")*

**Correction proposée** :

```diff
- {{before-snippet-or-description}}
+ {{after-snippet-or-description}}
```

**Effort** : {{effort}} *(XS < 15min · S < 1h · M < demi-journée · L < journée · XL > 1 jour)*

---

## 🟡 Friction — {{friction-count}} item(s)

*Ralentit mais l'utilisateur arrive au bout. À planifier ce sprint.*

### 🟡 1. {{title}}

**Règle violée** : {{nielsen-or-framework-reference}}

**Le problème** : {{problem}}

**Recommandation** : {{what-to-change}}

**Effort** : {{effort}}

---

## 🟢 Polish — {{polish-count}} item(s)

*Micro-améliorations, hiérarchie fine. À traiter quand tu as de la marge.*

### 🟢 1. {{title}}

{{short-description}} — {{effort}}

---

## ⭐ Ce qui marche déjà bien

{{2-3-genuine-strengths}}

Pas de flatterie — mentionne uniquement ce qui est **réellement** solide. C'est important pour que l'équipe sache quoi préserver pendant les changements.

---

## 🎯 Ce que je ferais cette semaine

Les 3 items qui donnent le **maximum d'impact** pour le minimum d'effort :

1. **{{item-1-title}}** ({{item-1-effort}}) — {{item-1-expected-impact}}
2. **{{item-2-title}}** ({{item-2-effort}}) — {{item-2-expected-impact}}
3. **{{item-3-title}}** ({{item-3-effort}}) — {{item-3-expected-impact}}

Total : **{{total-effort-this-week}}** pour passer d'un score **{{current-score}}** à environ **{{projected-score}} / 100**.

---

## 🔍 Ce qui échappe à cet audit

Certaines dimensions nécessitent une observation humaine ou de la data réelle :

- [ ] **Taux de drop-off réel** par étape (requires analytics data)
- [ ] **Heat maps** des interactions (Hotjar / Plausible pro)
- [ ] **Tests utilisateurs** qualitatifs (5-user study minimum)
- [ ] **Performance perçue** sur connexion lente (test manuel devtools)
- [ ] **Charge d'attention réelle** (eye tracking, si applicable)
- [ ] **Voice tone** global de l'app (nécessite revue editorial/brand)

---

## 📖 Frameworks référencés dans ce rapport

- [Nielsen's 10 Usability Heuristics](https://www.nngroup.com/articles/ten-usability-heuristics/)
- {{additional-frameworks-cited}} *(Hick's law, Fogg B=MAT, Baymard benchmarks, etc.)*

---

*Rapport généré par [UX Review](https://github.com/cherifskr/ux-review) · skill Claude Code*
*Par [Chérif Sikirou](https://cherifsikirou.com)*
