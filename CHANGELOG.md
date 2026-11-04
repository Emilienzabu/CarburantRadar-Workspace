# Changelog

Uniquement les modifications **réellement effectuées**. Format : date, élément, statut.

## 2026-11-04 (suite)

- Audit statique de `video/` : mise à jour de `audits/audit_videos.md`, `codes/worker_video.md`, `strategie/mesure_performance.md`, `produit/donnees_et_sources.md`, `AVANCEMENT.md` et `journal/2026-11-04.md` (branche `workspace-audit-video`, pull request à fusionner par Émilien). Aucune modification du dépôt de production, aucune exécution du générateur.

## 2026-11-04

- Création de la structure du workspace (32 fichiers), PR #1 fusionnée par Émilien. TERMINÉ.
- Worker `carburant-mcp` passé en version 1.1.0 : paramètre optionnel `repo` sur tous les outils, liste blanche `CarburantRadar` / `CarburantRadar-Workspace`, défaut `CarburantRadar`. Code préparé par Claude, déployé par Émilien (RAPPORTÉ PAR L'UTILISATEUR). Effet VÉRIFIÉ : écriture réussie sur le Workspace.
- Lecture seule du dépôt de production pour documenter : `README.md`, `SEO_REPORT.md`, `video/generate_video.py`, listing de la racine et de `video/`. Aucune modification du dépôt de production.
