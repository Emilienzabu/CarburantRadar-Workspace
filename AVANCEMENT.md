# Avancement

État au 2026-11-07, complété le 2026-11-12 pour le seul chantier radar (V76) : les sessions du 2026-11-08 n'avaient pas mis ce fichier à jour (voir [journal/2026-11-08.md](journal/2026-11-08.md)). Ce fichier est mis à jour en fin de session lorsque le travail le concerne. Statuts : voir [REGLES_DE_TRAVAIL.md](REGLES_DE_TRAVAIL.md).

## EN COURS

| Chantier | Détail | Statut / source |
|---|---|---|
| Radar CarburantRadar (prototype V76 : classement par coût total, Top 10, garage, snapshot France) | Intégration **isolée** dans `radar-v76/` du dépôt de production : copie fidèle de l'archive (75 fichiers, SHA-256), Worker candidat snapshot France V2 immuable (nouveau Worker séparé), API garage par compte, migrations D1 candidates, documentation, rollback. Session : [journal/2026-11-12.md](journal/2026-11-12.md) | EN COURS : **PR #39 ouverte, non fusionnée** (branche `claude/radar-v76-2026-11-12`, seul `radar-v76/` modifié). 541/541 + 61/61 tests sur clone propre (SQLite émule D1, Map émule R2) : VERIFIÉ. Rien déployé ; `release-gate` : dix preuves réelles absentes, **pas prêt**. Fusion déconseillée sans décision (GitHub Pages rendrait le dossier public) |
| Sécurisation des publications vidéo | Garde temporaire : toute publication limitée au format astuce (D-016, mesure liée à l'audit E0). PR #33 du dépôt de production (3 fichiers, 18 tests, workflow inchangé). Détail : [journal/2026-11-06.md](journal/2026-11-06.md) | PR #33 **fusionnée dans `main`** (commit de fusion `d40c3c3`, VÉRIFIÉ par clone le 2026-11-07). Effet réel au premier run : voix, Worker, YouTube, Instagram **non vérifiés** |
| Intégration de l'archive V100 (encodage Reels, contrôle avant publication, envois incertains/partiels, schéma anti-doublon candidat) | PR #34 du dépôt de production, branche `claude/v100-integration-2026-11-07` (4 commits, seul `video/` modifié, 85 tests OK sur un clone de la branche). Rapport : [audits/AUDIT_V100_2026-11-07.md](audits/AUDIT_V100_2026-11-07.md) ; session : [journal/2026-11-07.md](journal/2026-11-07.md) | EN COURS : PR #34 **ouverte, non fusionnée** (aucun effet en production). Schéma SQL **non validé sur Cloudflare D1** (testé sous SQLite seulement) |
| Protection anti-doublon durable | Schéma candidat `video/ledger/0001_video_ledger.sql` (non appliqué) ; branchement côté Worker `video-automation` + D1 ; impossible dans le générateur seul (exécuteur sans stockage durable) | Conception et schéma candidat. **Bloqué** : code du Worker, essai sur une base D1 de test (par Émilien) |
| Statistiques des vidéos et attribution | Collecte YouTube/Instagram, enregistrement durable à 24 h, 48 h, 7 j, 30 j, suivi des visites et inscriptions ; apprentissage non activé avant validation sur données suffisantes (D-016) | Conception seulement. **Bloqué** : code du Worker `video-automation` et portées OAuth réelles non disponibles pour Claude |
| Mission vidéo acquisition | Faire du générateur (`video/` + Worker `video-automation`) un canal d'acquisition ; intégration progressive autorisée (D-016) | EN COURS, RAPPORTÉ PAR L'UTILISATEUR |
| Correction géographique de `video/donnees.py` | Remplacer le filtre ignoré (audit E0) ; méthode à valider (voir [audits/AUDIT_E0_E1_2026-11-05.md](audits/AUDIT_E0_E1_2026-11-05.md)). Module autonome `video/geo.py` prêt (PR #34, 11 tests), **non branché** | Branchement non fait : attend la preuve stricte d'exhaustivité de C (diagnostic v4), un essai sur l'API réelle (champ `geom` non vérifié depuis le bac à sable) et la validation d'Émilien. Ligne à corriger : commune de repli = ville annoncée (contraire à D-014) |
| Workspace documentaire | Complétion des fichiers marqués À CONFIRMER (création terminée) | EN COURS |
| Diagnostics de données | Cellules A (fuseau XML/API), B (vidéo `--demo` + TTS), C (parité XML/API) ; résultat connu : station 56100009, gazole 2,179 € identique sur XML, API et site officiel (03/11/2026 11:58:50). Le fuseau de l'API est désormais VÉRIFIÉ en UTC (audit E1) | Partiellement couvert par l'audit E0/E1 ; cellules A/B/C RAPPORTÉES PAR L'UTILISATEUR |

## TERMINÉ

| Élément | Source |
|---|---|
| PR #33 (garde astuce) fusionnée dans `main` du dépôt de production | VÉRIFIÉ (clone, commit de fusion `d40c3c3`, 2026-11-07) |
| PR du Workspace de la session du 2026-11-06 (audit E0/E1, D-014 à D-016) fusionnée | VÉRIFIÉ (journal du 2026-11-06 lu sur `main` du Workspace le 2026-11-07) |
| Tests V100 reproduits en environnement isolé : 295 Python, 3 JavaScript | VÉRIFIÉ (2026-11-07). Ne prouve pas la compatibilité avec la production |
| Diagnostic E0/E1 exécuté (2026-11-05, script v3, 426 requêtes) et analysé : [audits/AUDIT_E0_E1_2026-11-05.md](audits/AUDIT_E0_E1_2026-11-05.md) | VÉRIFIÉ (résultats réels) |
| Protocole de mémoire partagée (D-012) fusionné dans `main` | VÉRIFIÉ (relecture de `main` le 2026-11-06 : README et journal du 2026-11-05 présents) |
| Paquet ChatGPT du 2026-11-04 intégré dans `main` | VÉRIFIÉ (journal/2026-11-05.md sur `main`) |
| Architecture multi-pays (un dossier + `index.html` par pays, sélecteur de pays à la racine) | RAPPORTÉ PAR L'UTILISATEUR ; dossiers présents : VÉRIFIÉ |
| Espagne (route `/es`) et Italie (route `/it`, stockage D1) | RAPPORTÉ PAR L'UTILISATEUR ; pages ES/IT présentes dans le rapport SEO : VÉRIFIÉ |
| Correctifs notification (clic ouvre la station), scope du service worker, accordéon du menu, hreflang, page `/guide/` | RAPPORTÉ PAR L'UTILISATEUR |
| Refonte SEO du générateur de pages villes, fusionnée le 2026-09-30 | RAPPORTÉ PAR L'UTILISATEUR ; `SEO_REPORT.md` présent : VÉRIFIÉ |
| Véhicules multiples et classement par coût total (France, Espagne, Italie) | VÉRIFIÉ (SEO_REPORT : « appliqué » pour les 3 pays) |
| Correction du mot « l'instant » qui cassait 3 pages villes françaises | RAPPORTÉ PAR L'UTILISATEUR |
| Connecteur `carburant-mcp` v1.1.0 avec paramètre `repo` (liste blanche de 2 dépôts) | VÉRIFIÉ (création de branche testée sur le Workspace le 2026-11-04) |

## À CONFIRMER (état incertain)

- Portage sur `espagne/` et `italie/` : menu en 4 onglets, bouton « Installer l'application », tutoriel de démarrage, bouton Snapchat, messages de géolocalisation distincts, ville précise (géocodage inverse). Notés « en attente » dans des sessions antérieures ; peuvent avoir été faits depuis. À vérifier dans le code.
- Option de rayon 50 km : le README de production la liste encore ; une note ancienne dit qu'elle a été abandonnée (D-007). À vérifier.
- Alertes : demande « priorité super importante » du 2026-10-14 (nom renommé dans la notification, clic vers la station) ; une correction du service worker est rapportée, la partie Worker n'est pas confirmée.
- Origine de l'écart 1080 × 1920 → 480 × 854 : le fichier **généré** est bien 1080 × 1920 H.264 (VÉRIFIÉ par rendus réels les 2026-11-06 et 2026-11-07 ; aucune mise à l'échelle dans le code) ; l'écart est donc après la génération : HYPOTHÈSES (Worker, retraitement YouTube ou Instagram), Worker non lu. L'audio du fichier généré était en 96 kHz, hors spécification Meta (corrigé dans la PR #34) : lien avec le 480 × 854 non établi. Manque : où le 480 × 854 a été observé (artefact GitHub, YouTube, Instagram).
- Depuis quand l'API ignore `geofilter.distance`, et quelles vidéos déjà publiées sont concernées : à vérifier sur les vidéos publiées (adresses du top 3 contre la ville annoncée).
- Pagination de `within_distance` au-delà de 100 résultats : non testée.
- Qualité de la voix française, synchronisation des sous-titres, rythme : non évalués (service de voix inaccessible depuis le bac à sable de Claude).
- Radar V76 : format réel de l'export `exports/json` (route, forme de `geom`, champs `*_maj`), plafond `offset+limit` de 10 000 de l'API Explore, limites Workers (CPU 10 ms, 50 sous-requêtes) sur le compte d'Émilien, politique d'usage du serveur de démonstration OSRM : HYPOTHÈSES / À CONFIRMER (détail dans [journal/2026-11-12.md](journal/2026-11-12.md)).

## BLOQUÉ / problèmes ouverts

| Problème | Statut |
|---|---|
| Filtre géographique `geofilter.distance` ignoré par l'API : formats « ville » et « classement » non fiables (données nationales, même échantillon pour toutes les villes) | VÉRIFIÉ (2026-11-05) ; mitigé par la garde astuce (PR #33 fusionnée, VÉRIFIÉ) ; correction des données non faite |
| Accès de Claude : le connecteur ne fusionne pas, ne lit ni n'écrit `.github/`, n'a pas d'outil Cloudflare ; `run_workflow` ne lance que le workflow Pages | VÉRIFIÉ par les outils disponibles (2026-11-06) ; la fusion et le déploiement passent par Émilien |
| Code du Worker `video-automation` non disponible pour Claude : bloque l'origine du 480 × 854, l'anti-doublon durable et les statistiques | VÉRIFIÉ (aucun outil de lecture Cloudflare) ; Émilien doit fournir le code (sans secret) |
| Code du Worker `carburant-proxy` non disponible pour Claude (ni dans le dépôt de production, ni dans le Workspace) : bloque le raccordement du garage radar à l'authentification réelle (format des sessions KV inconnu) | VÉRIFIÉ (lecture du dépôt le 2026-11-12) ; liste de ce qui manque : `radar-v76/docs/PROXY_WORKER_CHANGES.md` (PR #39) ; Émilien doit fournir le code sans secret |
| Anti-doublon : le générateur seul ne peut pas empêcher le relancement manuel d'un créneau déjà publié (exécuteur sans stockage durable) | VÉRIFIÉ (lecture du workflow) ; solution = Worker + D1 |
| Mesure `total_count` après curseur manquante (erreur gzip du diagnostic v3) : exhaustivité stricte de la référence C non démontrée | VÉRIFIÉ ; correction = diagnostic v4, à autoriser |
| Google Search Console : « Impossible de lire le sitemap » (`sitemap_1.xml` et `sitemap_2.xml`, contenu identique) | RAPPORTÉ PAR L'UTILISATEUR (2026-10-08) ; état actuel À CONFIRMER |
| Italie : source officielle indisponible au dernier rapport SEO (délai dépassé sur le CSV du ministère), cache de secours en HTTP 404 ; pages historiques conservées | VÉRIFIÉ (SEO_REPORT, données du 03/11/2026) |

## PROPOSITIONS EN ATTENTE

Aucune n'est une décision. Une proposition passe en décision seulement avec l'accord explicite d'Émilien ([DECISIONS.md](DECISIONS.md)), sauf pour le périmètre déjà couvert par D-016.

| Proposition | Origine / date | Statut | Remarque |
|---|---|---|---|
| Radar V76 : retenir le contrat snapshot (curseur numérique) pour la V2 ; fournir le code de `carburant-proxy` pour raccorder le garage ; créer D1/R2 **de test** et mesurer sur Cloudflare réel ; décider du sort de `radar-v76/` avant fusion (GitHub Pages) | Claude, 2026-11-12 | PROPOSITION | Détail : [journal/2026-11-12.md](journal/2026-11-12.md) et `radar-v76/docs/` (PR #39) |
| Brancher le schéma `video/ledger/0001_video_ledger.sql` dans `video-automation` (réservation du créneau avant publication, `needs_reconciliation` sans réessai) après lecture du Worker et essai sur une base D1 **de test** | Claude, 2026-11-07 | PROPOSITION | Détail : [audits/AUDIT_V100_2026-11-07.md](audits/AUDIT_V100_2026-11-07.md), sections 5 et 6 ; création de la base par Émilien |
| Faire exécuter les tests `video/tests` par un workflow et empêcher le lancement manuel d'un créneau déjà publié | Claude, 2026-11-07 | PROPOSITION | Modification de `.github/workflows` : hors des droits de Claude |
| Brancher `video/geo.py` dans `donnees.py` (même méthode géographique que la proposition E0/E1) | Claude, 2026-11-07 | PROPOSITION | Après validation de la méthode et essai sur l'API réelle |
| Architecture des statistiques : nouveau Worker `video-stats` + D1 (enregistrement des publications avec clé unique, collecte planifiée, suivi des visites) ou modification de `video-automation` | Claude, 2026-11-06 | PROPOSITION | Détail dans [journal/2026-11-06.md](journal/2026-11-06.md) ; dépend de la lecture du code de `video-automation` et d'Émilien (création de la base et des secrets) |
| Diagnostic E0/E1 version 4 (lecture gzip, `--seulement-b`, `--grand-rayon`) puis preuve stricte d'exhaustivité de C | Claude, 2026-11-05 | PROPOSITION | Voir l'audit E0/E1, section 6 |
| Méthode géographique de référence pour `donnees.py` : `within_distance` (B) ou export complet + Haversine ; seuils de fraîcheur par carburant ; tolérance sur les dates futures | Claude, 2026-11-05 | PROPOSITION | Audit E0/E1, sections 5 et 7 ; D-014 à respecter |
| Enrichir le catalogue des conseils (7 aujourd'hui) avec des contenus validés par Émilien ; historique et rotation durables (D-015) | Claude, 2026-11-06 | PROPOSITION | À 2 publications par jour, chaque conseil revient tous les 3,5 jours |
| Plan de corrections et d'améliorations CarburantRadar (vidéo, Workers, alertes, comptes, stats, tests ; ordre P0 à P2) | ChatGPT, 2026-11-04 (paquet) | PROPOSITION | Paquet intégral : [journal/2026-11-05.md](journal/2026-11-05.md) ; lots à valider un par un |
| Point d'accès MCP restreint pour ChatGPT : secret distinct, Workspace seul, poussée seulement sur des branches `chatgpt/*`, sans `run_workflow` ni suppression ; Émilien fusionne toujours | Claude, 2026-11-04 | PROPOSITION | Modification du Worker `carburant-mcp` : **non autorisée pour le moment** (D-013) |
| Outils en lecture seule pour `carburant-mcp` : lister branches, PR et commits | Claude, 2026-11-04 | PROPOSITION | Même contrainte (D-013) |
| Tester la lecture réelle du Workspace par le connecteur GitHub de ChatGPT | Claude, 2026-11-04 | PROPOSITION | Aucune modification technique nécessaire |
| Ajouter dans [INVENTAIRE_TECHNIQUE.md](INVENTAIRE_TECHNIQUE.md) un renvoi vers le registre des versions de [codes/README.md](codes/README.md) | Claude, 2026-11-04 | PROPOSITION | Fichier non inclus dans la PR de protocole validée |
| Dédoublonner : résultat de la cellule C, source italienne indisponible, audience | Claude, 2026-11-04 | PROPOSITION | Évite les dérives entre copies |
| Re-confirmer D-007 (périmètre) et D-008 (refus de Claude Code, devenue en partie obsolète avec le connecteur) | Claude, 2026-11-04 | PROPOSITION | Décisions anciennes, à revalider par Émilien |

Autres idées non décidées : [produit/idees_et_ameliorations.md](produit/idees_et_ameliorations.md).

## EN ATTENTE D'INTÉGRATION

Paquets de transfert ChatGPT → Claude et travaux de ChatGPT non encore intégrés dans `main`. Statuts : EN ATTENTE DE TRANSMISSION, EN ATTENTE D'INTÉGRATION, INTÉGRÉ (définitions : [REGLES_DE_TRAVAIL.md](REGLES_DE_TRAVAIL.md), section 3). Un paquet n'est jamais INTÉGRÉ parce qu'il est reçu ou parce qu'une PR existe : seulement après fusion et relecture de `main`.

| Paquet | Auteur | Reçu le | Statut | PR | Prochaine action |
|---|---|---|---|---|---|
| ZIP `carburantradar_etape76.zip` (prototype Radar V51 à V76 ; notes de passation V75/V76) | ChatGPT | 2026-11-12 | EN ATTENTE D'INTÉGRATION (partielle : prototype et code candidat dans le dossier isolé `radar-v76/`, aucune intégration dans l'application ; preuves réelles du `release-gate` absentes) | PR #39 (`CarburantRadar`, non fusionnée) ; PR du Workspace `claude/radar-v76-2026-11-12` | Émilien décide du sort de `radar-v76/` (Pages) puis fusionne ; Claude relit `main` et met à jour ce statut. L'archive n'est pas conservée dans le Workspace (détenue par Émilien) |
| ZIP `CarburantRadar_Audit_Production_V100.zip` (modules V94 à V100 : portes de livraison vidéo, protections de publication, schémas D1) | ChatGPT | 2026-11-07 | EN ATTENTE D'INTÉGRATION (partielle : portes de contrôle consolidées et branchées, schéma D1 consolidé en candidat non appliqué ; vérification distante, réconciliation et reste de l'archive non intégrés) | PR #34 (`CarburantRadar`, non fusionnée) ; PR du Workspace `claude/audit-v100-2026-11-07` | Émilien fusionne ; Claude relit `main` puis met à jour ce statut. L'archive n'est pas conservée dans le Workspace (détenue par Émilien) |
| ZIP `carburant_handoff_20261106` : garde astuce, laboratoire de statistiques (35 tests locaux sur données simulées), plan de collecte | ChatGPT | 2026-11-06 | garde astuce INTÉGRÉE (PR #33 fusionnée, `main` relu le 2026-11-07) ; collecteurs, stockage, attribution et apprentissage EN ATTENTE D'INTÉGRATION (non intégrés) | PR #33 fusionnée | Suite après lecture du Worker `video-automation` |

Note : un paquet EN ATTENTE DE TRANSMISSION n'existe que côté ChatGPT et Émilien ; il n'apparaît ici qu'une fois remis à Claude.

Voir aussi [audits/](audits/README.md) et [produit/idees_et_ameliorations.md](produit/idees_et_ameliorations.md).
