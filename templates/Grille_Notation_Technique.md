# Grille de notation — Pilier A (Technique & Performance)

> Utilisée par le chef A0 pour agréger les scores des **9 analystes** (A1→A9) en un score A /10. L'agent **A-COL (Collecteur)** n'est pas noté : il fournit la collecte live partagée. Chaque analyste note sa dimension /10 selon les barèmes ci-dessous, puis A0 applique la pondération.

## Pondération du pilier A
| Sous-agent | Dimension | Poids |
|---|---|---|
| A1 | Performance & Core Web Vitals | 20 % |
| A2 | Poids, images & médias | 12 % |
| A3 | Polices & render-blocking | 8 % |
| A4 | Cache, compression & livraison | 10 % |
| A5 | Stack, CMS & hébergement | 10 % |
| A6 | Liens morts, 404 & intégrité | 15 % |
| A7 | Sécurité & en-têtes HTTP | 8 % |
| A8 | JavaScript, console & réseau | 10 % |
| A9 | Mobile & compatibilité technique | 7 % |

`Score A = Σ (note_sous-agent /10 × poids) / 100` → arrondi à 1 décimale. `Σ poids = 100 %`.

> ⚠️ Un blocage critique plafonne le score A quoi qu'il arrive (CTA principal en 404, LCP > 6 s, certificat SSL invalide, site non responsive) : A0 le signale au lieu de moyenner.

---

## Barème A1 — Performance & Core Web Vitals (mesuré, jamais deviné)
Référence Core Web Vitals (Google) : LCP ≤ 2,5 s bon / 2,5-4 s à améliorer / > 4 s mauvais · INP ≤ 200 ms / 200-500 / > 500 · CLS ≤ 0,1 / 0,1-0,25 / > 0,25.
- 9-10 : LCP < 2,5 s mobile, CLS < 0,1, INP bon, score PageSpeed mobile ≥ 90.
- 7-8 : Core Web Vitals globalement « bon », score mobile 70-89.
- 4-6 : 1-2 métriques « à améliorer », score mobile 50-69.
- 0-3 : LCP > 4 s ou score mobile < 50.
⚠️ Toute note s'appuie sur des **mesures** (PageSpeed mobile+desktop, CrUX terrain, ou Timing live). Sans mesure → `Non vérifié`.

## Barème A2 — Poids, images & médias
- 9-10 : poids page maîtrisé (< 1,5 Mo), images WebP/AVIF dimensionnées, lazy-load + srcset présents.
- 7-8 : bonne base, 1-2 images lourdes ou format ancien isolé.
- 4-6 : plusieurs images sur-dimensionnées / PNG-JPG lourds, pas de lazy-load, poids 3-5 Mo.
- 0-3 : médias très lourds (> 5 Mo), images non optimisées massives, vidéo lourde en autoplay.
⚠️ Poids **réel par ressource** (panneau réseau), jamais estimé. « images lourdes » = Ko à l'appui.

## Barème A3 — Polices & render-blocking
- 9-10 : polices préchargées/optimisées, `font-display: swap`, peu/pas de CSS/JS bloquant, ressources minifiées et différées.
- 7-8 : bonne base, 1-2 ressources bloquantes.
- 4-6 : web-fonts bloquantes (FOIT), plusieurs CSS/JS render-blocking, peu de minification.
- 0-3 : rendu fortement bloqué, FOIT marqué, nombreux scripts synchrones.
⚠️ « Bloquant » confirmé via réseau / opportunités Lighthouse (render-blocking resources), pas déduit du seul HTML.

## Barème A4 — Cache, compression & livraison
- 9-10 : Brotli/gzip actif, cache long sur statiques, HTTP/2-3, CDN edge, bundling propre.
- 7-8 : compression OK, politique de cache perfectible.
- 4-6 : pas de CDN, compression partielle, cache court/absent sur statiques.
- 0-3 : aucune compression, aucun cache, HTTP/1.1, livraison non optimisée.
⚠️ En-têtes **réels** (`Content-Encoding`, `Cache-Control`) lus via réseau ; toute « absence » double-vérifiée (Règle 4).

## Barème A5 — Stack, CMS & hébergement
- 9-10 : stack moderne adaptée (framework récent, hébergement perf, TTFB < 200 ms).
- 7-8 : stack correcte, TTFB moyen (200-600 ms).
- 4-6 : stack datée ou mal dimensionnée, TTFB élevé (> 600 ms).
- 0-3 : stack lourde/obsolète pénalisant nettement (builder lourd mal configuré, TTFB > 1 s).
⚠️ CMS/techno détectés via signatures (en-têtes, `generator`, empreintes), TTFB **mesuré**.

## Barème A6 — Liens morts, 404, redirections & intégrité
- 9-10 : zéro lien mort/404, redirections propres (HTTPS, www cohérent), pas de mixed content.
- 7-8 : 1-2 liens secondaires cassés, sinon propre.
- 4-6 : plusieurs liens morts OU 404 sur pages clés OU mixed content.
- 0-3 : navigation cassée (CTA principal mort, menu 404).
⚠️ Chaque lien mort = URL + statut HTTP réel (double-check Règle 4).

## Barème A7 — Sécurité & en-têtes HTTP
- 9-10 : HTTPS valide, HSTS, CSP présente, en-têtes de sécurité (X-Frame-Options, X-Content-Type-Options), cookies sécurisés.
- 7-8 : HTTPS OK, 1-2 en-têtes manquants.
- 4-6 : plusieurs en-têtes de sécurité absents, pas de HSTS/CSP.
- 0-3 : certificat invalide/expiré, mixed content massif, aucune protection.
⚠️ En-têtes lus en live (réseau / outil type securityheaders) ; « absent » double-vérifié.

## Barème A8 — JavaScript, console & réseau
- 9-10 : console propre, aucune requête échouée, scripts tiers maîtrisés.
- 7-8 : 1-2 warnings mineurs.
- 4-6 : erreurs JS visibles, quelques 404 ressources, scripts tiers lourds.
- 0-3 : erreurs JS bloquantes, nombreuses requêtes échouées, fonctionnalités cassées.
⚠️ Erreurs lues via `read_console_messages` / `read_network_requests`, jamais supposées.

## Barème A9 — Mobile & compatibilité technique
- 9-10 : viewport correct, rendu technique mobile sain, pas de scroll horizontal technique, compatibilité large.
- 7-8 : 1-2 soucis techniques mineurs sur mobile.
- 4-6 : viewport mal configuré OU rendu mobile technique dégradé (zoom forcé, breakpoints cassés).
- 0-3 : site non responsive techniquement, viewport absent, inutilisable sur mobile.
⚠️ Testé en live à ~390 px + DOM (`<meta viewport>`). La **casse visuelle responsive** est à **B7** ; ici c'est le **technique** (viewport, breakpoints, compat).
