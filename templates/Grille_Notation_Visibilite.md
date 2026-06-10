# Grille de notation — Pilier C (Visibilité SEO / GEO)

> Utilisée pour condenser la sortie du pilier C (l'ex-kit ROSO, 11 agents) en **un seul score C /10** exploitable par l'orchestrateur global (pondération A/B/C). Le pilier C produit déjà un score /10 par agent (Phase 6 de `piliers/C_VISIBILITE/01_MASTER_ORCHESTRATOR.md`) et un Score de Visibilité IA /100 (Agent 09bis) ; cette grille dit **comment on les agrège**, en réutilisant la pondération native du kit (Agent 10) pour ne pas inventer une seconde logique.

## Formule
`Score C = Σ (score_agent /10 × poids_agent) / Σ (poids_agent)` → arrondi à 1 décimale.

L'Agent 09bis produit un score **/100** : le convertir en /10 (`/10 = score_100 / 10`) avant de l'injecter dans la formule.

---

## Pondération — mode Complet (les 11 agents)
Reprend exactement les poids natifs du kit (cf. `piliers/C_VISIBILITE/agents/10_Master_Final_Report.md`, étape 2) :

| Agent | Dimension | Poids |
|---|---|---|
| 01 | Data Collector (méta-agent) | 0,5 |
| 02 | Stratégie / positionnement | 1 |
| 03 | Homepage on-page | 1,5 |
| 04 | Keywords / intentions | 1 |
| 05 | Analyse concurrentielle | 1 |
| 06 | Content SEO/GEO | 1,5 |
| 07 | SEO technique / données structurées | 1,5 |
| 08 | Autorité / brand / local | 1,5 |
| 09 | Visibilité IA / plan d'action | 1,5 |
| 09bis | Auto-Test IA (score /100 → /10) | 1 |

`Σ poids = 12`.

---

## Pondération — mode Express (prospection : 03 + 07 + 09 + 09bis)
C'est le mode recommandé pour la prospection. On garde les **mêmes poids** que ci-dessus, restreints aux agents lancés :

| Agent | Dimension | Poids |
|---|---|---|
| 03 | Homepage on-page | 1,5 |
| 07 | SEO technique / données structurées | 1,5 |
| 09 | Visibilité IA / plan d'action | 1,5 |
| 09bis | Auto-Test IA (score /100 → /10) | 1 |

`Σ poids = 5,5`.

> Si un audit Express est lancé sans 09bis (pas de test IA), `Σ poids = 4,5` sur 03/07/09. Toujours indiquer dans l'audit les agents réellement exécutés (Règle 8 — honnêteté de couverture).

---

## Lecture du score C (cohérente avec les grilles A et B)
- **9-10** : SEO/GEO très propre (on-page solide, technique SEO saine, bonne citabilité IA).
- **7-8** : bonne base, optimisations possibles (schema partiel, GEO perfectible).
- **4-6** : lacunes nettes (title/meta faibles, schema absent, peu de citabilité IA).
- **0-3** : critique (non indexé, pas de sitemap/robots, invisible des IA, contenu pauvre).

⚠️ Garde-fous (rappel) : aucun score sans source (Règle 2), toute absence (schema, sitemap, indexation) double-vérifiée (Règle 4), incohérence score↔détail re-vérifiée avant agrégation (Règle 7). Le **Score de Visibilité IA /100** reste affiché tel quel dans l'audit (section PILIER C), en plus de sa contribution au score C /10.
