# GitHub Actions

Le connecteur `carburant-mcp` interdit volontairement l'accès à `.github/` : **le contenu des workflows n'a pas pu être lu** pendant l'écriture de ce workspace. Tout détail de configuration ci-dessous est donc À CONFIRMER, sauf mention contraire.

## Connu

| Élément | Détail | Statut |
|---|---|---|
| Workflow « Générer les pages villes » | Fichier `generate-city-pages.yml` ; lancé par le connecteur via `run_workflow` | VÉRIFIÉ (nom lu dans le code du connecteur) |
| Sortie du workflow | `SEO_REPORT.md`, pages `france/`, `espagne/`, `italie/`, sitemaps, notification IndexNow | VÉRIFIÉ (SEO_REPORT) |
| Workflow vidéo | Le générateur mentionne « relance le workflow » en cas de voix indisponible ; existence et planning du workflow vidéo | VÉRIFIÉ pour la mention ; le reste : À CONFIRMER |
| Action verte sur la branche `seo-refonte` (2026-09-30) | | RAPPORTÉ PAR L'UTILISATEUR |

## À documenter dès que possible

- Déclencheurs (cron, manuel), horaires, permissions du jeton du workflow.
- Secrets utilisés par chaque workflow (noms seulement).
- Règle D-009 : aucun changement de workflow sans autorisation explicite ([../DECISIONS.md](../DECISIONS.md)).
