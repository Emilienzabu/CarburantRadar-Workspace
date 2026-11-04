# Codes

Notes sur le code du projet. Le code de production vit dans `Emilienzabu/CarburantRadar` ; ce dossier documente, il ne remplace pas le dépôt.

| Fichier | Sujet |
|---|---|
| [cellules_python.md](cellules_python.md) | Cellules de diagnostic Python (A, B, C) |
| [worker_proxy.md](worker_proxy.md) | Worker Cloudflare `carburant-proxy` |
| [worker_video.md](worker_video.md) | Worker `video-automation` et générateur `video/` |
| [github_actions.md](github_actions.md) | Workflows GitHub Actions |

Règle : ne jamais coller de secret dans ces fichiers ([../SECURITE_ET_SECRETS.md](../SECURITE_ET_SECRETS.md)). Le code complet des Workers n'est pas dans le dépôt de production (il vit dans Cloudflare) : toute description ici est RAPPORTÉ PAR L'UTILISATEUR ou À CONFIRMER tant que le code n'a pas été relu.
