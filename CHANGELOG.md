# Changelog

Uniquement les modifications **réellement effectuées**. Format : date, [auteur] élément, statut. Un paquet de transfert intégré n'est noté INTÉGRÉ qu'après fusion et relecture de `main` ([REGLES_DE_TRAVAIL.md](REGLES_DE_TRAVAIL.md), section 3).

## 2026-11-04

- [Claude] Création de la structure du workspace (32 fichiers) sur la branche `workspace-init`. TERMINÉ côté écriture. Fusion : les 32 fichiers sont présents sur `main` (VÉRIFIÉ par lecture le 2026-11-04) ; la PR elle-même n'est pas consultable via le connecteur, la branche `workspace-init` existe toujours.
- [Claude] Worker `carburant-mcp` passé en version 1.1.0 : paramètre optionnel `repo` sur tous les outils, liste blanche `CarburantRadar` / `CarburantRadar-Workspace`, défaut `CarburantRadar`. Code préparé par Claude, déployé par Émilien (RAPPORTÉ PAR L'UTILISATEUR). Effet VÉRIFIÉ : création de branche réussie sur le Workspace.
- [Claude] Lecture seule du dépôt de production pour documenter : `README.md`, `SEO_REPORT.md`, `video/generate_video.py`, listing de la racine et de `video/`. Aucune modification du dépôt de production.
- [Claude] Introduction du protocole de mémoire partagée ChatGPT/Claude (D-012, D-013) : règles de travail complètes, statuts de transmission, paquet de transfert, journal quotidien par assistant, objectifs et principes, registre des versions, règles de sécurité des échanges. Préparé sur la branche `protocole-memoire` (une PR, un commit, partie de `main` au commit `ee89cfe`). Effet réel à partir de la fusion par Émilien. Aucun code de production, Worker, secret, droit GitHub ni workflow modifié.
