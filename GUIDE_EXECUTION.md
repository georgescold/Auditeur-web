# 🚀 Guide d'exécution — Auditeur site Essort

Comment lancer un audit, dans les 3 cas d'usage. **L'audit ne se déclenche jamais tout seul** : c'est toi qui le lances dans Cowork (voir § « Quand l'audit a-t-il lieu ? » en bas).

---

## 0. Prérequis (à faire une seule fois)

| Prérequis | Pourquoi | Comment |
|---|---|---|
| **Cowork** (app de bureau Claude) | C'est l'environnement où tournent les agents | Ouvrir l'app Claude desktop |
| **Claude in Chrome activé** | Méthode PRIMAIRE de l'audit : rendu visuel réel, test interactif, mobile, exécution JS, console/réseau. Sans lui, l'audit tourne en mode dégradé (beaucoup de `Non vérifié`) | Activer l'extension/le contrôle Chrome dans Cowork |
| **Connexion Airtable** (mode CRM uniquement) | Lire le lead et écrire « Audit complet » | Connecter le MCP Airtable au compte « essort » |
| **Ouvrir ce dossier** dans Cowork | Pour que Claude lise les agents | Ouvrir `Auditeur site Essort` |

> ⚠️ Sans Claude in Chrome, l'auditeur **fonctionne quand même** mais beaucoup de constats passent en `Non vérifié` (perf live, captures visuelles, test interactif). Pour un audit fiable → Chrome obligatoire.

---

## 1. Point d'entrée unique : l'orchestrateur

Quel que soit le mode, on parle **toujours** à l'orchestrateur global : `01_ORCHESTRATEUR_AUDIT.md`. C'est lui (et lui seul) qui lance les 3 piliers, fusionne, calcule le score /100 et — en mode CRM — écrit dans Airtable.

Phrase d'amorçage type (à coller dans Cowork, dossier ouvert) :

> « Tu es l'orchestrateur de l'auditeur Essort (lis `01_ORCHESTRATEUR_AUDIT.md`). [puis la consigne du mode choisi ci-dessous]. »

---

## 2. CAS A — Auditer UN site précis (mode URL libre)

Pour auditer un site à la volée, en décrivant de quoi il s'agit et son marché. **N'écrit rien dans Airtable** : restitue le rapport à l'écran.

**Prompt à coller :**

```
Tu es l'orchestrateur de l'auditeur Essort (lis 01_ORCHESTRATEUR_AUDIT.md et 00_REGLES_COMMUNES.md).
Audite ce site en mode URL libre :
- URL : https://exemple-client.fr
- Activité : [ex. menuisier-agenceur haut de gamme, fabrication sur-mesure]
- Cible / marché : [ex. particuliers CSP+ et architectes d'intérieur, région Lyon]
- Profondeur pilier C : Express  (ou : Complet)
Restitue l'Audit complet au format templates/format_audit_complet.md (ne touche pas à Airtable).
```

**Ce qui se passe :** A (Technique), B (Visuel), C (Visibilité) tournent en parallèle sur l'URL → fusion → score /100 → rapport affiché.

> Le contexte « Activité » + « Cible / marché » est important : il calibre la profondeur par secteur (cf. `00_REGLES_COMMUNES.md` §4) et l'attendu (ex. e-commerce = tunnel + données Product ; local = mobile + Google Business).

---

## 3. CAS B — Auditer des PROSPECTS Airtable (mode CRM)

C'est le mode « usine ». L'orchestrateur lit le lead dans le CRM, récupère l'URL depuis **« Lien site web »**, audite, et **écrit le résultat dans la colonne « Audit complet »** (et rien d'autre).

### B.1 — Un lead précis
```
Tu es l'orchestrateur de l'auditeur Essort (lis 01_ORCHESTRATEUR_AUDIT.md).
Mode CRM. Audite le lead « [Nom du lead] » de la table « CRM leads reporting » (base essort).
Profondeur pilier C : Express.
Écris le résultat dans « Audit complet », n'écris rien d'autre.
```

### B.2 — Un lot de prospects (audit « intelligent »)
```
Tu es l'orchestrateur de l'auditeur Essort (lis 01_ORCHESTRATEUR_AUDIT.md).
Mode CRM, traitement par lot. Prends les leads de la vue « Loys - email & LinkedIn »
qui ONT un « Lien site web » et dont « Audit complet » est ENCORE VIDE.
Audite-les un par un (profondeur Express), écris « Audit complet » pour chacun,
et SAUTE ceux déjà audités. Fais-moi un récap final (lead par lead : score + écrit oui/non).
```

### Ce qui est déjà programmé dans ce mode (état actuel)
- ✅ Lit la base **essort** (`appSL5Gx3DXKbGq15`) / table **CRM leads reporting** (`tblzafpMMq7I90IK6`).
- ✅ Récupère l'URL à auditer depuis **« Lien site web »**, lit **« Nom »** et **« Paint point »** (le Paint point n'est qu'une *piste* à confirmer en live, jamais recopiée).
- ✅ Lance A + B + C en parallèle, fusionne, calcule le score /100.
- ✅ Écrit **uniquement** dans **« Audit complet »** (`fldJM8MKlLTUj2ZPL`).
- ✅ **Anti-doublon** : ne ré-audite pas un lead dont « Audit complet » est déjà rempli (sauf si tu le demandes explicitement, ou si le site a changé).
- ❌ N'écrit **rien d'autre** : pas de Tag, pas d'Awareness, pas d'email (ce n'est pas son rôle — ça, c'est le SDR et le système de mails).
- ❌ **Aucune sélection autonome** des prospects : c'est TOI qui définis le périmètre (un lead, une vue, un lot). « Intelligent » = il sait quoi lire, quoi écrire et quoi sauter — pas choisir seul quels prospects méritent un audit.

> La « sélection automatique » (ex. : surveiller la vue et auditer tout nouveau lead avec site) **n'existe pas encore**. Si tu la veux, c'est une évolution simple à ajouter (routine planifiée) — demande-la.

---

## 4. Profondeur du pilier C : Express vs Complet

| Mode | Agents C lancés | Pour |
|---|---|---|
| **Express** *(défaut prospection)* | 03 (homepage) + 07 (technique SEO) + 09 (visibilité IA) + 09bis (auto-test IA) | Réchauffage de prospects : l'essentiel actionnable |
| **Complet** | les 11 agents C | Audit SEO/GEO de fond (lead à fort potentiel) |

Les piliers **A (Technique) et B (Visuel) tournent toujours en entier** (collecteur + 9 analystes chacun) ; le mode ne joue que sur C.

---

## 5. Ce qui se passe sous le capot (résumé)

```
Orchestrateur
 ├─ Pilier A : A-COL (collecte live) → A1..A9 en parallèle → score A/10
 ├─ Pilier B : B-COL (captures)      → B1..B9 en parallèle → score B/10
 └─ Pilier C : 03+07+09(+09bis) ou 11 agents → score C/10
        ↓ contrôle qualité (sources, double-check, anti-contradiction)
        ↓ fusion au format format_audit_complet.md + score /100
        ↓ (mode CRM) écriture « Audit complet »  |  (mode URL) rapport à l'écran
```

Soit ~**30 agents** sur un audit complet A+B+C. Le collecteur de chaque pilier sert à amortir : une seule passe de collecte partagée, réutilisée par les 9 analystes.

---

## 6. Quand l'audit a-t-il lieu dans le process ? (important)

**Aujourd'hui : à la demande, lancé par toi dans Cowork. Aucun déclenchement automatique** (pas de cron, pas de routine, pas de hook — vérifié).

Place de l'audit dans la chaîne Essort de bout en bout :

```
1. [TOI, ici] AUDIT du site  ───────────►  écrit « Audit complet »
2. Agent Paint point          ───────────►  génère la fiche SDR depuis « Audit complet »
3. Edouardo (SDR)             ───────────►  appelle, remplit Notes / Tags / Awareness
4. Agent Mails & LinkedIn     ───────────►  écrit Email 1 / Email 2 / LinkedIn
```

Donc l'audit est la **toute première brique** : on le lance **dès qu'un lead a un site web, idéalement avant l'appel d'Edouardo**, pour que :
- le **Paint point** (fiche SDR) puisse en être tiré pour l'appel,
- puis le **système de mails** s'appuie dessus + sur les Notes de l'appel.

En pratique pour la prospection : quand un nouveau lot de leads arrive dans la vue de travail avec un « Lien site web », tu lances le **CAS B.2** (lot, Express) → tous les « Audit complet » se remplissent → la suite du funnel peut tourner.

---

## 7. Limites & mode dégradé

- **Sans Claude in Chrome** → perf live, captures, test interactif et console indisponibles : beaucoup de `Non vérifié`, confiance globale plafonnée. À éviter pour un vrai audit.
- **Site protégé (Cloudflare 403, anti-bot)** → l'audit continue en notant le blocage exact ; les points non vérifiables restent `Non vérifié` (jamais inventés).
- **Périmètre minimal** (cf. `00_REGLES_COMMUNES.md`) : home desktop+mobile + 1-2 pages clés. En deçà, la confiance est plafonnée à « Moyen » et la raison notée en tête d'audit.
- **Jamais d'envoi ni d'action réelle** : l'auditeur ne soumet aucun formulaire, ne réserve rien, n'écrit aucun email. Sa seule sortie = « Audit complet ».
