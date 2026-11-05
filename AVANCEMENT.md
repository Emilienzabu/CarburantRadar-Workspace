# Avancement

État au 2026-11-05. Ce fichier est mis à jour en fin de session lorsque le travail le concerne. Statuts : voir [REGLES_DE_TRAVAIL.md](REGLES_DE_TRAVAIL.md).

## EN COURS

| Chantier | Détail | Statut / source |
|---|---|---|
| Mission vidéo acquisition | Faire du générateur (`video/` + Worker `video-automation`) un canal d'acquisition ; règle : audit, puis plan validé, avant toute modification | EN COURS, RAPPORTÉ PAR L'UTILISATEUR |
| Workspace documentaire | Création de ce dépôt (32 fichiers) : contenu présent sur `main`, VÉRIFIÉ par lecture le 2026-11-04. La branche `workspace-init` existe toujours ; l'état de la PR n'est pas consultable via le connecteur. Complétion des fichiers marqués À CONFIRMER : à faire | Création : TERMINÉ (résultat vérifié sur `main`) ; complétion : EN COURS |
| Protocole de mémoire partagée | Branche `protocole-memoire`, une seule PR, protocole validé par Émilien le 2026-11-04 (D-012) | EN COURS jusqu'à la fusion ; passer à TERMINÉ seulement après relecture de `main` |
| Diagnostics de données | Cellules A (fuseau XML/API), B (vidéo `--demo` + TTS), C (parité XML/API) | EN COURS ; seul résultat connu : station 56100009, gazole 2,179 € identique sur XML, API et site officiel (03/11/2026 11:58:50), RAPPORTÉ PAR L'UTILISATEUR |

## TERMINÉ

| Élément | Source |
|---|---|
| Architecture multi-pays (un dossier + `index.html` par pays, sélecteur de pays à la racine) | RAPPORTÉ PAR L'UTILISATEUR ; dossiers présents : VÉRIFIÉ |
| Espagne (route `/es`) et Italie (route `/it`, stockage D1) | RAPPORTÉ PAR L'UTILISATEUR ; pages ES/IT présentes dans le rapport SEO : VÉRIFIÉ |
| Correctifs notification (clic ouvre la station), scope du service worker, accordéon du menu, hreflang, page `/guide/` | RAPPORTÉ PAR L'UTILISATEUR |
| Refonte SEO du générateur de pages villes, fusionnée le 2026-09-30 | RAPPORTÉ PAR L'UTILISATEUR ; `SEO_REPORT.md` présent : VÉRIFIÉ |
| Véhicules multiples et classement par coût total (France, Espagne, Italie) | VÉRIFIÉ (SEO_REPORT : « appliqué » pour les 3 pays) |
| Correction du mot « l'instant » qui cassait 3 pages villes françaises | RAPPORTÉ PAR L'UTILISATEUR |
| Connecteur `carburant-mcp` v1.1.0 avec paramètre `repo` (liste blanche de 2 dépôts) | VÉRIFIÉ (création de branche testée sur le Workspace le 2026-11-04) |

## À CONFIRMER (état incertain)

- Portage sur `espagne/` et `italie/` : menu en 4 onglets, bouton « Installer l'application », tutoriel de démarrage, bouton Snapchat, messages de géolocalisation distincts, ville précise (géocodage inverse). Notés « en attente » dans des sessions antérieures ; peuvent avoir été faits depuis. À vérifier dans le code.
- Option de rayon 50 km : le README de production la liste encore ; une note ancienne dit qu'elle a été abandonnée. À vérifier.
- Alertes : demande « priorité super importante » du 2026-10-14 (nom renommé dans la notification, clic vers la station) ; une correction du service worker est rapportée, la partie Worker n'est pas confirmée.
- Filtre géographique `geofilter.distance` du générateur vidéo : le paquet ChatGPT du 2026-11-04 le juge douteux, une note ancienne indique qu'il fonctionnait. Test réel requis (voir [journal/2026-11-05.md](journal/2026-11-05.md)).
- Origine de l'écart 1080 × 1920 (généré, VÉRIFIÉ dans `rendu.py`) → 480 × 854 (reçu, RAPPORTÉ) : HYPOTHÈSE côté Worker `video-automation` ou récupération ; Worker non lu.

## BLOQUÉ / problèmes ouverts

| Problème | Statut |
|---|---|
| Google Search Console : « Impossible de lire le sitemap » (`sitemap_1.xml` et `sitemap_2.xml`, contenu identique) | RAPPORTÉ PAR L'UTILISATEUR (2026-10-08) ; état actuel À CONFIRMER |
| Italie : source officielle indisponible au dernier rapport SEO (délai dépassé sur le CSV du ministère), cache de secours en HTTP 404 ; pages historiques conservées | VÉRIFIÉ (SEO_REPORT, données du 03/11/2026) |

## PROPOSITIONS EN ATTENTE

Aucune n'est une décision. Une proposition passe en décision seulement avec l'accord explicite d'Émilien ([DECISIONS.md](DECISIONS.md)).

| Proposition | Origine / date | Statut | Remarque |
|---|---|---|---|
| Plan de corrections et d'améliorations CarburantRadar (vidéo, Workers, alertes, comptes, stats, tests ; ordre P0 à P2) | ChatGPT, 2026-11-04 (paquet) | PROPOSITION | Détail et paquet intégral : [journal/2026-11-05.md](journal/2026-11-05.md). Plan technique par lots à préparer puis à valider lot par lot |
| Point d'accès MCP restreint pour ChatGPT : secret distinct, Workspace seul, poussée seulement sur des branches `chatgpt/*`, sans `run_workflow` ni suppression ; Émilien fusionne toujours | Claude, 2026-11-04 | PROPOSITION | Nécessite de modifier le Worker `carburant-mcp` : **non autorisé pour le moment** (D-013). Compatibilité ChatGPT avec une URL à secret (au lieu d'OAuth) : À CONFIRMER |
| Outils en lecture seule pour `carburant-mcp` : lister branches, PR et commits (pour connaître les dernières modifications et relever des SHA de commit) | Claude, 2026-11-04 | PROPOSITION | Même contrainte : modification du Worker non autorisée pour le moment (D-013) |
| Tester la lecture réelle du Workspace par le connecteur GitHub de ChatGPT (32 fichiers, fraîcheur, branches non fusionnées) | Claude, 2026-11-04 | PROPOSITION | Aucune modification technique nécessaire ; résultat À CONFIRMER |
| Ajouter dans [INVENTAIRE_TECHNIQUE.md](INVENTAIRE_TECHNIQUE.md) un renvoi vers le registre des versions de [codes/README.md](codes/README.md) | Claude, 2026-11-04 | PROPOSITION | Fichier non inclus dans la PR de protocole validée |
| Dédoublonner : résultat de la cellule C (AVANCEMENT, `cellules_python`, `donnees_et_sources`), source italienne indisponible (AVANCEMENT, `audit_international`), audience (CONTEXTE_GLOBAL, `acquisition_utilisateurs`) | Claude, 2026-11-04 | PROPOSITION | Évite les dérives entre copies |
| Re-confirmer D-007 (périmètre) et D-008 (refus de Claude Code, devenue en partie obsolète avec le connecteur) | Claude, 2026-11-04 | PROPOSITION | Décisions anciennes, à revalider par Émilien |

Autres idées non décidées : [produit/idees_et_ameliorations.md](produit/idees_et_ameliorations.md).

## EN ATTENTE D'INTÉGRATION

Paquets de transfert ChatGPT → Claude et travaux de ChatGPT non encore intégrés dans `main`. Statuts : EN ATTENTE DE TRANSMISSION, EN ATTENTE D'INTÉGRATION, INTÉGRÉ (définitions : [REGLES_DE_TRAVAIL.md](REGLES_DE_TRAVAIL.md), section 3). Un paquet n'est jamais INTÉGRÉ parce qu'il est reçu ou parce qu'une PR existe : seulement après fusion et relecture de `main`.

| Paquet | Auteur | Reçu le | Statut | PR | Prochaine action |
|---|---|---|---|---|---|
| Plan de corrections et d'améliorations CarburantRadar (paquet daté 2026-11-04) | ChatGPT | 2026-11-05 | EN ATTENTE D'INTÉGRATION | branche `integration-paquet-chatgpt-2026-11-05` | Émilien fusionne la PR ; Claude relit `main`, passe le paquet à INTÉGRÉ (CHANGELOG) et retire cette ligne |

Note : un paquet EN ATTENTE DE TRANSMISSION n'existe que côté ChatGPT et Émilien ; il n'apparaît ici qu'une fois remis à Claude.

Voir aussi [audits/](audits/README.md) et [produit/idees_et_ameliorations.md](produit/idees_et_ameliorations.md).
