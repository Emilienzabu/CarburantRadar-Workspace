# Inventaire technique

Mis à jour : 2026-11-04. Chaque ligne indique sa certitude. Détails de code : [codes/README.md](codes/README.md).

## Frontend

| Élément | Détail | Statut |
|---|---|---|
| App | HTML/CSS/JS vanilla, un fichier `index.html` par pays, aucun framework | VÉRIFIÉ (README) |
| Hébergement | GitHub Pages | VÉRIFIÉ (README, fichier CNAME présent) |
| Service worker | `service-worker.js` unique partagé par les 3 pays | RAPPORTÉ PAR L'UTILISATEUR ; fichier présent : VÉRIFIÉ |
| PWA | `manifest.json`, dossier `icons/`, APK `CarburantRadar.apk` à la racine | VÉRIFIÉ (listing) |
| Cartographie | Leaflet + OpenStreetMap, itinéraires OSRM, géocodage Nominatim | VÉRIFIÉ (README) |
| Tracking | `track.js` (non lu), Google Analytics (gtag) | README : VÉRIFIÉ ; contenu de `track.js` : À CONFIRMER |
| Administration | dossier `admin/` : graphique d'usage, tableau des comptes | RAPPORTÉ PAR L'UTILISATEUR |

## Pages SEO générées

- `generate.py` (racine) et dossier `generator/` : génération des pages villes, départements, régions, ville + carburant, hubs, sitemaps, `SEO_REPORT.md`. VÉRIFIÉ (présence ; rapport lu).
- Sitemaps : `sitemap_1.xml` et `sitemap_2.xml`, `robots.txt`. VÉRIFIÉ (présence).
- Notification IndexNow aux moteurs après génération. VÉRIFIÉ (SEO_REPORT).

## Backend (Cloudflare)

| Élément | Détail | Statut |
|---|---|---|
| Worker `carburant-proxy` | Proxy API, comptes, favoris, alertes push, `/es`, `/it`, `/track`, routes `/admin/*` | RAPPORTÉ PAR L'UTILISATEUR (code hors dépôt) |
| KV `USERS`, `SUBS` | Comptes ; abonnements aux alertes | RAPPORTÉ PAR L'UTILISATEUR |
| D1 `DB_ITALIE` | Table `stations_it` ; table `usage_days` (usage quotidien) | RAPPORTÉ PAR L'UTILISATEUR |
| Cron | Alertes quotidiennes `10 5 * * *` (UTC) | RAPPORTÉ PAR L'UTILISATEUR (ancien) |
| Worker `video-automation` | Endpoint `POST /api/upload`, profil `carburant` | VÉRIFIÉ (appel dans `video/generate_video.py`) ; code du Worker : À CONFIRMER |
| Worker `carburant-mcp` v1.1.0 | Outils : `get_file`, `create_branch`, `push_files`, `create_pull_request`, `delete_branch`, `run_workflow`, `list_runs`, `get_run_jobs`, `get_job_logs` ; paramètre `repo` ; liste blanche `CarburantRadar` et `CarburantRadar-Workspace` | VÉRIFIÉ (code lu, branche créée sur le Workspace) |

Gardes-fous de `carburant-mcp` (VÉRIFIÉ dans le code) : lien contenant un secret, aucune écriture sur `main`/`master`, dossier `.github/` inaccessible, chemins avec `..` refusés, 60 fichiers max par commit, 1 000 000 caractères max par fichier, `run_workflow` limité au dépôt de production.

## Génération vidéo (dépôt de production, dossier `video/`)

Fichiers : `generate_video.py`, `audio.py`, `donnees.py`, `rendu.py`, `musique.py`, `requirements.txt`, `.gitignore`. VÉRIFIÉ (listing). Fonctionnement : [audits/audit_videos.md](audits/audit_videos.md).

## CI

Workflows GitHub Actions : voir [codes/github_actions.md](codes/github_actions.md). Contenu non lu (dossier protégé côté connecteur) : À CONFIRMER.

## Sources de données

Voir [produit/donnees_et_sources.md](produit/donnees_et_sources.md).
