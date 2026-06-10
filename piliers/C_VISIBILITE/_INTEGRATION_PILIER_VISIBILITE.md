# Intégration — Pilier C « Visibilité » dans l'auditeur Essort

> À lire AVANT de lancer le pilier C. Ce dossier est l'ancien kit SEO/GEO (11 agents), repris **tel quel** et intégré comme **pilier Visibilité** de l'auditeur Essort. Seules les mentions de marque ont été remplacées par « Essort ». Ce fichier explique comment il se branche dans le nouveau système, sans rien casser de son fonctionnement interne.

## Ce qui change (adaptation au nouveau système)

1. **Sortie qui compte = la synthèse SEO/GEO**, pas les 2 PDF client.
   Dans le kit d'origine, l'**Agent 10 (Master Final Report)** produisait 2 PDF client-facing (Audit + Plan d'implémentation). **Dans l'auditeur Essort, on n'en a pas besoin** : l'auditeur ne produit que la colonne « Audit complet » (interne). Donc :
   - Pour la prospection, on **n'exécute pas l'Agent 10** (pas de PDF client).
   - Ce qui remonte à l'orchestrateur global = le **rapport fusionné SEO/GEO** (Phase 6 du `01_MASTER_ORCHESTRATOR.md`) : scores par agent, diagnostic, top priorités, score Visibilité IA. L'orchestrateur global en fait la **section « PILIER C »** de l'« Audit complet ».
   - Si un jour on veut un livrable SEO/GEO autonome, l'Agent 10 reste disponible (rien n'est supprimé).

2. **Audit interne, pas client.** La Règle 8 du pilier C (vocabulaire client-friendly / glossaire) visait des PDF client. Dans l'« Audit complet » interne, **on a le droit d'être technique** (c'est l'agent mails, séparé, qui vulgarisera plus tard pour le prospect). On garde donc la rigueur SEO/GEO du kit, sans s'obliger à tout vulgariser.

3. **Profondeur pilotée par l'orchestrateur global :**
   - **Express** (prospection) : Agents **03** (homepage on-page) + **07** (technique SEO, schema, indexation, sitemap/robots/llms.txt) + **09** (visibilité IA + grille GEO) + **09bis** (auto-test IA, enchaîné après 09 — toujours au minimum Claude + Web Search Google). C'est l'essentiel actionnable.
   - **Complet** : toute la séquence des 11 agents (`01_MASTER_ORCHESTRATOR.md`), pour un audit SEO/GEO approfondi.

   **Condensation en un score C /10** (pour la pondération A/B/C de l'orchestrateur global) : voir `../../templates/Grille_Notation_Visibilite.md`. Elle réutilise la pondération native du kit (Agent 10) selon le mode lancé (Complet : Σ poids = 12 ; Express : Σ poids = 5,5). Le Score de Visibilité IA /100 (09bis) reste affiché en plus dans la section PILIER C.

4. **Pas d'écriture CRM par le pilier C.** Comme tous les agents, le pilier C **ne touche pas Airtable**. Seul l'orchestrateur global écrit « Audit complet ».

5. **Cohérence avec les autres piliers :**
   - La **performance** chiffrée appartient au pilier **A** (A1). L'Agent 07 du pilier C peut la mentionner mais **s'aligne sur les mesures de A1** (pas de second chiffre contradictoire).
   - Le **contraste / accessibilité** appartient au pilier **B** (B4).
   - Le pilier C garde : SEO on-page, sitemap/robots/canonical/llms.txt, schema/JSON-LD, indexation, GEO/IA, maillage interne, keywords, contenu, autorité/avis/local.

## Ce qui ne change pas
- Le fonctionnement interne du kit (ses 8 règles communes, son triple statut, ses protocoles anti-faux-négatif, ses grilles) reste **identique et pertinent**. On ne le réécrit pas.
- Le pilier C a son **propre** `00_REGLES_COMMUNES.md` (dans ce dossier), historique du kit. En cas de doute, les **règles communes globales** de l'auditeur (`../../00_REGLES_COMMUNES.md`) priment au niveau de l'orchestration ; les règles du kit s'appliquent à l'intérieur du pilier C.

## Lancement du pilier C
- Point d'entrée : `01_MASTER_ORCHESTRATOR.md` (mode Express ou Complet selon la consigne de l'orchestrateur global).
- Sortie attendue par l'orchestrateur global : le **rapport fusionné SEO/GEO** (scores agents + diagnostic + top priorités + score Visibilité IA + « Non vérifié » à confirmer), à insérer en section PILIER C.
