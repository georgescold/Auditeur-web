# Template — « Audit complet » (sortie unique de l'auditeur Essort)

> C'est le format EXACT que l'orchestrateur global écrit dans la colonne **« Audit complet »** (`fldJM8MKlLTUj2ZPL`) du CRM Airtable, après fusion des 3 piliers. Audit **interne**, exhaustif, technique, justifié. Pas de vulgarisation client ici (c'est l'agent mails qui vulgarise ensuite). Zéro tiret cadratin.

---

```
AUDIT ESSORT — [nom du site] ([secteur / cible]) — vérifié en LIVE (Chrome, [date])
Score global : XX/100   |   Confiance globale : Élevé / Moyen / Faible
Périmètre : [pages testées] · desktop + mobile · [N] liens cliqués

═══════════════════════════════════════════════════════════
0. CONTEXTE & CIBLE
- Ce que fait la boîte, sa cible, ce qui compte pour SON marché.
- 1-2 infos OSINT utiles (founder, actu, secteur).
- Stack/CMS détecté (confirmé par A3).

═══════════════════════════════════════════════════════════
PILIER A — TECHNIQUE & PERFORMANCE   (score A : X/10)   [9 analystes A1→A9, collecte partagée A-COL]
A1. Performance & Core Web Vitals (chiffrés, source PageSpeed/live) : LCP … / INP … / CLS … / FCP … / Speed Index … / poids … / requêtes … · scores mobile+desktop → conséquences business.
A2. Poids, images & médias : poids total, formats (WebP/AVIF vs PNG/JPG), images sur-dimensionnées, lazy-load, srcset, vidéos.
A3. Polices & render-blocking : web-fonts, font-display, CSS/JS bloquant, minification.
A4. Cache, compression & livraison : Brotli/gzip, cache statiques, HTTP/2-3, CDN, bundling.
A5. Stack, CMS & hébergement : CMS/framework détecté, hébergeur, TTFB mesuré, architecture.
A6. Liens morts & intégrité : [liste 404 / boutons morts / ancres cassées / redirections / mixed content], chacun avec l'URL et le statut HTTP.
A7. Sécurité & en-têtes HTTP : SSL/TLS, HSTS, CSP, en-têtes de sécurité, cookies.
A8. JavaScript, console & réseau : erreurs JS, requêtes échouées, coût des scripts tiers.
A9. Mobile & compatibilité technique : viewport, breakpoints, scroll horizontal technique, compat navigateurs.

═══════════════════════════════════════════════════════════
PILIER B — VISUEL, DESIGN & ACCESSIBILITÉ   (score B : X/10)   [9 analystes B1→B9, captures partagées B-COL]
B1. Direction artistique & identité : esthétique, cohérence de marque (logo/couleurs/typo), épure, modernité. NOTE DESIGN /10 justifiée, comparée aux standards haut de gamme.
B2. Typographie & hiérarchie visuelle : système typo, échelle, graisses, interlignage, lisibilité, hiérarchie (≠ Hn SEO).
B3. Couleur, palette & harmonie : palette relevée, harmonie, cohérence d'usage, ambiance sectorielle.
B4. Layout, grille & espacement : grille, espacements, alignements, densité, composition.
B5. Imagerie & médias visuels : qualité/authenticité des visuels (vrais vs stock/IA), iconographie, art direction.
B6. Contraste & accessibilité WCAG : ratios AA/AAA mesurés, tap targets, focus, labels, navigation clavier de base.
B7. Bugs visuels & responsive : incohérences, éléments cassés/tassés, scroll horizontal, rendu mobile vs desktop, overflow (vérifiés à l'écran).
B8. Détection « fait par IA » & site daté : patterns génératifs, templates sans âme, signaux d'ancienneté (verdict + preuves).
B9. UX, parcours & conversion + microcopy : visibilité des CTA, clarté above-the-fold, friction, navigation, microcopy d'interface.

═══════════════════════════════════════════════════════════
PILIER C — VISIBILITÉ (SEO / GEO)   (score C : X/10)
- SEO on-page : title, meta, Hn, alt, OG.
- Technique SEO : robots.txt, sitemap, canonical, llms.txt, schema/JSON-LD, indexation (site:).
- GEO / IA : citabilité, structure pour LLM, contenu.
- Maillage interne, keywords/intentions, autorité/avis/local (selon profondeur lancée).
- Score Visibilité IA si Agent 09bis lancé.

═══════════════════════════════════════════════════════════
✅ CE QUI MARCHE DÉJÀ (sincère, 2-4 points, techniques en priorité)
- …

🎯 TOP 5 PRIORITÉS (du plus impactant, tous piliers confondus)
| # | Point | Pilier | Conséquence | Ce qu'on ferait |
|---|-------|--------|-------------|------------------|

⚠️ POINTS À NE PAS SORTIR (mémoire anti-erreur pour l'agent mails)
- [Faux positifs écartés en live, jugements code infirmés à l'écran, éléments déjà corrigés.]

═══════════════════════════════════════════════════════════
VERDICT EN 1 PHRASE + ce que la maquette Essort changerait.

───────────────────────────────────────────────────────────
ANNEXE — Traçabilité
- Sources : [Chrome live / PageSpeed / Web Fetch / WebSearch / outils externes]
- Confiance par pilier : A … / B … / C …
- Éléments « Non vérifié » à confirmer : […]
```

---

## Calcul du score global /100

Pondération par défaut (ajustable selon le secteur par l'orchestrateur, en le notant) :
- **Technique (A)** : 35 %
- **Visuel (B)** : 35 %
- **Visibilité (C)** : 30 %

`Score global = round( (scoreA/10*35) + (scoreB/10*35) + (scoreC/10*30) )`. Chaque score de pilier est la synthèse pondérée de ses sous-agents (voir grilles).

> ⚠️ Le score ne sert qu'en interne (priorisation). Il ne « tue » jamais le besoin : même un bon score laisse des axes (DA, sur-mesure, refonte) mis en avant (cf. Règle 6 des règles communes).
