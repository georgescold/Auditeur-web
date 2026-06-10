# 🔬 Auditeur site Essort

**Système d'audit de site web autonome — Version 1.0 (10 juin 2026)**

Système **indépendant** du système de mails & marketing d'Essort. Sa **seule sortie** est la colonne **« Audit complet »** du CRM Airtable. Il **n'écrit aucun email**, ne produit **aucun PDF client**, n'envoie **rien**. Il audite, il remplit « Audit complet », point.

L'audit couvre **3 piliers lancés en parallèle**, chacun avec ses sous-agents sur-optimisés, sur le modèle structurel du pilier Visibilité (ex-kit SEO/GEO).

---

## 🎯 Ce que produit l'auditeur
Un **« Audit complet » interne, exhaustif, technique et justifié** : perf chiffrée, liens morts, stack, DA notée, bugs visuels, détection IA/site daté, contraste WCAG, SEO/GEO. Avec, pour chaque point, un **statut** (Confirmé / Déduit / Non vérifié), un **score**, des **actions concrètes**, et une **mémoire anti-erreur** (« points à ne pas sortir ») qui protège l'agent mails en aval.

---

## 🧱 Architecture

```
Auditeur site Essort/
├── README.md                         ← ce fichier
├── 00_REGLES_COMMUNES.md             ← LA loi (8 garde-fous, LIVE, triple statut, anti-faux-positif)
├── 01_ORCHESTRATEUR_AUDIT.md         ← lance les 3 piliers EN PARALLÈLE, fusionne, écrit « Audit complet »
├── templates/
│   ├── format_audit_complet.md       ← format exact écrit dans le CRM + calcul du score /100
│   ├── Grille_Notation_Technique.md  ← pondération + barèmes pilier A
│   ├── Grille_Notation_Visuel.md     ← pondération + barèmes pilier B
│   └── Grille_Notation_Visibilite.md ← condensation du pilier C en un score C /10
└── piliers/
    ├── A_TECHNIQUE/                   ← chef A0 + collecteur + 9 analystes
    │   ├── A0_chef_technique.md       ← pilote A-COL puis A1→A9, fusionne, score A
    │   ├── A_COLLECTEUR.md               (collecte live partagée : PageSpeed, timing, réseau, console, en-têtes)
    │   ├── A1_performance_pagespeed.md   (PageSpeed + Core Web Vitals, mesuré)
    │   ├── A2_poids_images_medias.md     (poids page, formats/dimensionnement images, lazy-load, médias)
    │   ├── A3_polices_render_blocking.md (web-fonts, FOUT/FOIT, CSS/JS bloquant, minification)
    │   ├── A4_cache_compression_livraison.md (Brotli/gzip, cache, HTTP/2-3, CDN, bundling)
    │   ├── A5_stack_cms_hebergement.md   (CMS/framework, hébergement, TTFB, architecture)
    │   ├── A6_liens_morts_404.md         (liens morts, 404, redirections, mixed content, intégrité)
    │   ├── A7_securite_entetes_http.md   (SSL/TLS, HSTS, CSP, en-têtes de sécurité, cookies)
    │   ├── A8_javascript_console_reseau.md (erreurs JS, console, requêtes échouées, scripts tiers)
    │   └── A9_mobile_compatibilite_technique.md (viewport, breakpoints, compat — technique)
    ├── B_VISUEL/                      ← chef B0 + collecteur + 9 analystes
    │   ├── B0_chef_visuel.md          ← pilote B-COL puis B1→B9, fusionne, score B + note design
    │   ├── B_COLLECTEUR.md               (set de captures partagé : hero+scroll desktop & mobile)
    │   ├── B1_direction_artistique.md    (DA, cohérence marque, épure, modernité, note design)
    │   ├── B2_typographie_hierarchie.md  (système typo, échelle, hiérarchie visuelle, lisibilité)
    │   ├── B3_couleur_palette.md         (palette, harmonie, cohérence d'usage chromatique)
    │   ├── B4_layout_grille_espacement.md (grille, espacements, alignements, composition)
    │   ├── B5_imagerie_medias.md         (qualité/authenticité visuels, iconographie, art direction)
    │   ├── B6_contraste_wcag.md          (contraste mesuré, tap targets, focus, WCAG)
    │   ├── B7_bugs_responsive.md         (bugs visuels vérifiés à l'écran, responsive)
    │   ├── B8_detection_ia_site_date.md  (verdict global « fait par IA », site daté)
    │   ├── B9_ux_parcours_microcopy.md   (CTA, above-the-fold, parcours, microcopy d'interface)
    │   └── references_visuelles.md       (godly.website / siteinspire = standards haut de gamme)
    └── C_VISIBILITE/                  ← ex-kit SEO/GEO (11 agents), « Roso » → « Essort »
        ├── _INTEGRATION_PILIER_VISIBILITE.md  ← comment il se branche (À LIRE EN PREMIER)
        ├── 01_MASTER_ORCHESTRATOR.md
        ├── 00_REGLES_COMMUNES.md (propre au pilier C)
        ├── Outils_Verification_Externes.md
        ├── agents/ (01 à 10 + 09bis)
        └── templates/
```

---

## 🚀 Lancer un audit (dans Cowork, avec Claude in Chrome)

1. Ouvrir ce dossier dans **Cowork** (app de bureau Claude) avec **Claude in Chrome activé** (méthode primaire : visuel, test interactif, mobile, JS, console/réseau).
2. Donner à l'orchestrateur (`01_ORCHESTRATEUR_AUDIT.md`) soit un **lead Airtable**, soit une **URL** :
   - *« Audite le lead [Nom] de la vue Loys »* (Mode CRM → écrit « Audit complet »), ou
   - *« Audite https://exemple.fr (secteur : … ) »* (Mode URL libre → restitue le rapport).
3. L'orchestrateur lance **A, B, C en parallèle** (et leurs sous-agents en parallèle), contrôle la cohérence, fusionne au format `templates/format_audit_complet.md`, calcule le score /100, et écrit dans le CRM.
4. Profondeur du pilier C : **Express** (03+07+09 + 09bis enchaîné, pour la prospection) ou **Complet** (11 agents).

> Parallélisme : les 3 piliers sont **indépendants** (aucun ne dépend de la sortie d'un autre) → 100 % parallélisables. Dans A et B, le **collecteur** (A-COL / B-COL) tourne d'abord, puis les **9 analystes** (A1→A9 / B1→B9) sont indépendants et parallèles.

---

## ⚖️ Les règles d'or (détail dans `00_REGLES_COMMUNES.md`)
1. **Tout vérifier en LIVE** : aucun jugement cosmétique depuis le seul HTML (carrousels lazy-load, doublons invisibles, placeholders déjà remplacés). Le site a pu être refait.
2. **Chiffres sourcés** : aucun LCP / ratio / score inventé.
3. **Triple statut** partout : Confirmé / Déduit / Non vérifié.
4. **Double-check des affirmations négatives** (lien mort, bug, absence).
5. **Garde-fou interactif** : on teste l'UI, on ne **soumet jamais** un formulaire, on ne déclenche aucune action réelle.
6. **Créer le besoin sans le tuer** : jamais « rien à corriger » ; toujours 2-4 vrais positifs aussi.
7. **Un seul faux reproche = crédibilité morte.** Dans le doute, on retire ou on passe en « Non vérifié ».

---

## 🔗 Lien avec le système de mails
Les deux systèmes sont **séparés** mais reliés par le CRM : l'auditeur **écrit** « Audit complet » ; le système de mails (dossier « Audit et suivi ») **lit** « Audit complet » et en extrait quelques points vulgarisés pour le prospect. L'auditeur ne sait rien des mails ; le système de mails ne refait pas l'audit.
