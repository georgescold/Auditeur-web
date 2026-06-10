# Grille de notation — Pilier B (Visuel, Design & Accessibilité)

> Utilisée par le chef B0 pour agréger les **9 analystes** (B1→B9) en un score B /10 + une **note design justifiée**. L'agent **B-COL (Collecteur)** n'est pas noté : il fournit le set de captures partagé. Le jugement visuel est **subjectif par nature** : chaque note doit être **justifiée par des preuves visuelles concrètes** (captures, zones précises) et calée sur les **standards haut de gamme** (`references_visuelles.md`). Vérification LIVE obligatoire (Règle 5).

## Pondération du pilier B
| Sous-agent | Dimension | Poids |
|---|---|---|
| B1 | Direction artistique & identité de marque | 22 % |
| B2 | Typographie & hiérarchie visuelle | 10 % |
| B3 | Couleur, palette & harmonie | 8 % |
| B4 | Layout, grille & espacement | 12 % |
| B5 | Imagerie & médias visuels | 10 % |
| B6 | Contraste & accessibilité WCAG | 10 % |
| B7 | Bugs visuels & responsive | 12 % |
| B8 | Détection « fait par IA » & site daté | 8 % |
| B9 | UX, parcours & conversion + microcopy | 8 % |

`Score B = Σ (note_sous-agent /10 × poids) / 100` → arrondi à 1 décimale. `Σ poids = 100 %`.
La **note design /10** affichée dans l'audit = la note de **B1** (justifiée, comparée aux standards).

> ⚠️ Une casse visuelle nette (mobile inutilisable, illisibilité massive) plafonne le score B : B0 le signale au lieu de moyenner.

---

## Barème B1 — Direction artistique & identité de marque
- 9-10 : DA distinctive, sur-mesure, cohérente (grille, espacements, typo, palette), niveau référençable (godly/siteinspire).
- 7-8 : propre et cohérent, mais générique / peu mémorable.
- 4-6 : template reconnaissable, incohérences, manque d'épure ou de hiérarchie.
- 0-3 : visuellement daté ou brouillon, identité de marque faible/absente.

## Barème B2 — Typographie & hiérarchie visuelle
- 9-10 : système typo maîtrisé (échelle, interlignage, contraste de graisses), hiérarchie limpide, lisibilité excellente.
- 7-8 : typo propre, hiérarchie correcte, 1-2 tailles/longueurs de ligne limites.
- 4-6 : échelle typo incohérente, hiérarchie faible, interlignage/longueurs inconfortables.
- 0-3 : typographie chaotique, illisible, aucune hiérarchie.
⚠️ Jugé au **rendu réel à l'écran** ; distinct de la structure **Hn SEO** (= pilier C).

## Barème B3 — Couleur, palette & harmonie
- 9-10 : palette maîtrisée et harmonieuse, usage cohérent et intentionnel, ambiance alignée au secteur.
- 7-8 : palette correcte, 1-2 usages flottants.
- 4-6 : trop de couleurs OU palette incohérente OU sans identité.
- 0-3 : chaos chromatique, couleurs criardes/datées.
⚠️ Jugement esthétique justifié par captures ; le **ratio de contraste mesuré** est à **B6**.

## Barème B4 — Layout, grille & espacement
- 9-10 : grille rigoureuse, espacements rythmés, alignements nets, respiration maîtrisée.
- 7-8 : composition propre, 1-2 espacements irréguliers.
- 4-6 : alignements flottants, densité inégale, manque de grille/respiration.
- 0-3 : composition désordonnée, chevauchements, aucune grille perceptible.
⚠️ Vérifié à l'écran desktop + mobile ; la **casse responsive** (bugs) est à **B7**.

## Barème B5 — Imagerie & médias visuels
- 9-10 : visuels authentiques de qualité, iconographie cohérente, art direction soignée.
- 7-8 : bons visuels, 1-2 images stock/génériques.
- 4-6 : mix d'images stock/génériques, iconographie incohérente, qualité inégale.
- 0-3 : visuels stock/IA évidents, basse qualité, incohérents.
⚠️ Qualité/authenticité jugée **à l'écran** (Règle 5) ; le **poids/format technique** des images est à **A2**.

## Barème B6 — Contraste & accessibilité WCAG
Référence WCAG 2.1 : texte normal AA ≥ 4,5:1, grand texte AA ≥ 3:1, AAA ≥ 7:1.
- 9-10 : contrastes AA respectés partout, tap targets ≥ 44 px, labels présents, focus visible.
- 7-8 : AA respecté sur l'essentiel, 1-2 zones limites.
- 4-6 : plusieurs zones sous le seuil AA (texte gris clair sur blanc, CTA peu contrasté).
- 0-3 : contraste global insuffisant, illisibilité, aucun marqueur d'accessibilité.
⚠️ Ratios **mesurés** (luminance via JS / outil), pas estimés à l'œil.

## Barème B7 — Bugs visuels & responsive
- 9-10 : aucun bug, responsive impeccable desktop + mobile, zéro scroll horizontal.
- 7-8 : 1-2 imperfections mineures (léger débordement, image un peu étirée).
- 4-6 : plusieurs bugs visibles OU mobile clairement dégradé (éléments tassés, chevauchements).
- 0-3 : casse visuelle nette (overflow, composants superposés, mobile inutilisable).
⚠️ Chaque bug **vérifié à l'écran** (capture), pas déduit du code (Règle 5).

## Barème B8 — Détection « fait par IA » & site daté
Note INVERSÉE : 10 = aucun signal IA/daté ; 0 = manifestement généré IA ou très daté.
- 9-10 : aucun pattern génératif, aucun signe d'ancienneté, visuels authentiques.
- 7-8 : 1-2 éléments un peu génériques (1 visuel stock/IA), sinon authentique.
- 4-6 : patterns IA reconnaissables (visuels génératifs, copy « elevate your business ») OU signaux datés (effets 2010s, dégradés/ombres lourds).
- 0-3 : clairement template IA sans âme, ou site visiblement ancien non maintenu.
⚠️ Jugements à **confirmer en live + zoom** (Règle 5) ; on cite les preuves.

## Barème B9 — UX, parcours & conversion + microcopy
- 9-10 : CTA évidents et bien placés, above-the-fold clair, parcours fluide, microcopy nette et rassurante.
- 7-8 : parcours clair, 1-2 frictions mineures.
- 4-6 : CTA peu visibles, hiérarchie de conversion floue, microcopy générique, friction notable.
- 0-3 : aucun CTA clair, parcours confus, friction forte.
⚠️ Évalué à l'écran en **interactif sans soumission** (Règle 6) ; le **contenu/copy SEO** est à **C** : ici c'est l'**UX et la microcopy d'interface** (libellés de boutons, above-the-fold, parcours).
