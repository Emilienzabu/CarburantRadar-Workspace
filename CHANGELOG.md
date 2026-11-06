# Changelog

Uniquement les modifications **réellement effectuées**. Format : date, [auteur] élément, statut. Un paquet de transfert intégré n'est noté INTÉGRÉ qu'après fusion et relecture de `main` ([REGLES_DE_TRAVAIL.md](REGLES_DE_TRAVAIL.md), section 3).

## 2026-11-04

- [Claude] Création de la structure du workspace (32 fichiers) sur la branche `workspace-init`. TERMINÉ côté écriture. Fusion : les 32 fichiers sont présents sur `main` (VÉRIFIÉ par lecture le 2026-11-04) ; la PR elle-même n'est pas consultable via le connecteur, la branche `workspace-init` existe toujours.
- [Claude] Worker `carburant-mcp` passé en version 1.1.0 : paramètre optionnel `repo` sur tous les outils, liste blanche `CarburantRadar` / `CarburantRadar-Workspace`, défaut `CarburantRadar`. Code préparé par Claude, déployé par Émilien (RAPPORTÉ PAR L'UTILISATEUR). Effet VÉRIFIÉ : création de branche réussie sur le Workspace.
- [Claude] Lecture seule du dépôt de production pour documenter : `README.md`, `SEO_REPORT.md`, `video/generate_video.py`, listing de la racine et de `video/`. Aucune modification du dépôt de production.
- [Claude] Introduction du protocole de mémoire partagée ChatGPT/Claude (D-012, D-013) : règles de travail complètes, statuts de transmission, paquet de transfert, journal quotidien par assistant, objectifs et principes, registre des versions, règles de sécurité des échanges. Préparé sur la branche `protocole-memoire` (une PR, un commit, partie de `main` au commit `ee89cfe`). Effet réel à partir de la fusion par Émilien. Aucun code de production, Worker, secret, droit GitHub ni workflow modifié.

## 2026-11-05

- [Claude] Paquet de transfert ChatGPT du 2026-11-04 (plan de corrections) : INTÉGRÉ (journal du 2026-11-05 présent sur `main`, VÉRIFIÉ par relecture le 2026-11-06) ; protocole de mémoire partagée fusionné (README de `main` conforme, VÉRIFIÉ).
- [Claude] Script de diagnostic E0/E1 (versions 1 à 3, lecture seule, hors dépôts) remis à Émilien ; exécution réelle par Émilien le 2026-11-05 (version 3, 426 requêtes). Analyse archivée : [audits/AUDIT_E0_E1_2026-11-05.md](audits/AUDIT_E0_E1_2026-11-05.md). Aucune modification de production.

## 2026-11-06

- [Claude] Clone en lecture seule du dépôt de production dans le bac à sable de Claude (commit `c066bde`) ; exécution de tests et de rendus locaux. Aucune écriture sur `main`.
- [Claude] Dépôt de production : branche `securite-astuce-publication` (commits `e460a2b`, `e1f7ff2`) et PR #33 « Garde temporaire : toute publication vidéo limitée au format astuce ». **PR ouverte, non fusionnée** : aucun effet en production tant qu'Émilien ne la fusionne pas. Workflow, Worker, secrets inchangés.
- [Claude] Workspace : audit E0/E1, journal du 2026-11-06, décisions D-014 à D-016, avancement, registre des versions (branche `claude-2026-11-06-securisation-videos`, PR à fusionner par Émilien).
