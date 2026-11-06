# Codes

Notes sur le code du projet. Le code de production vit dans `Emilienzabu/CarburantRadar` ; ce dossier documente, il ne remplace pas le dépôt et ne duplique pas les fichiers de production.

| Fichier | Sujet |
|---|---|
| [cellules_python.md](cellules_python.md) | Cellules de diagnostic Python (A, B, C) |
| [worker_proxy.md](worker_proxy.md) | Worker Cloudflare `carburant-proxy` |
| [worker_video.md](worker_video.md) | Worker `video-automation` et générateur `video/` |
| [github_actions.md](github_actions.md) | Workflows GitHub Actions |

Règle : ne jamais coller de secret dans ces fichiers ([../SECURITE_ET_SECRETS.md](../SECURITE_ET_SECRETS.md)). Le code complet des Workers n'est pas dans le dépôt de production (il vit dans Cloudflare) : toute description ici est RAPPORTÉ PAR L'UTILISATEUR ou À CONFIRMER tant que le code n'a pas été relu.

## Registre des versions

Pour retrouver les bons codes et les bonnes versions sans qu'Émilien les renvoie. Un composant important = une ligne.

Règles :

- Ne jamais inventer un SHA de commit. Le connecteur `carburant-mcp` n'offre pas d'outil pour relever un commit ; **mais le dépôt de production est public** : un `git clone` en lecture seule depuis le bac à sable de Claude (domaine `github.com` autorisé) donne le code réel, `.github/` compris, et le SHA réel. Sans clone, écrire « non relevé (À CONFIRMER) » et noter la date et ce qui a été réellement lu.
- Mettre la ligne à jour chaque fois qu'un assistant relit le fichier ou le composant ; la date de vérification est celle de la lecture.
- « Lu » = contenu relu (VÉRIFIÉ pour cette date). « Présent » = seulement vu dans un listing.
- Le code de production reste la référence ; on ne le copie pas ici.

| Composant | Dépôt | Chemin | Branche | Dernier commit vérifié | Vérification | Rôle | Dépendances et points de vigilance |
|---|---|---|---|---|---|---|---|
| App France | `Emilienzabu/CarburantRadar` | `france/index.html` | `main` (À CONFIRMER) | non relevé (À CONFIRMER) | dossier présent (listing) ; contenu non lu | App PWA France | `service-worker.js`, Worker `carburant-proxy`, API officielle des prix |
| App Espagne | `Emilienzabu/CarburantRadar` | `espagne/index.html` | `main` (À CONFIRMER) | non relevé (À CONFIRMER) | dossier présent (listing) ; contenu non lu | App PWA Espagne | Route `/es` du Worker ; portage de fonctions France : À CONFIRMER |
| App Italie | `Emilienzabu/CarburantRadar` | `italie/index.html` | `main` (À CONFIRMER) | non relevé (À CONFIRMER) | dossier présent (listing) ; contenu non lu | App PWA Italie | Route `/it` du Worker, D1 ; source italienne indisponible au dernier rapport SEO |
| Service worker | `Emilienzabu/CarburantRadar` | `service-worker.js` | `main` (À CONFIRMER) | non relevé (À CONFIRMER) | présent (listing) ; contenu non lu | Cache et notifications, partagé par les 3 pays | Scope et clic de notification (correctifs rapportés) |
| Générateur de pages SEO | `Emilienzabu/CarburantRadar` | `generate.py`, `generator/` | `main` | `c066bde` | `generator/data_fr.py` lu le 2026-11-06 (clone en lecture seule) : télécharge l'export complet, décompresse le gzip, n'utilise pas `geofilter.distance` ; `SEO_REPORT.md` lu le 2026-11-04 | Pages villes, départements, régions, sitemaps | Workflow « Générer les pages villes » ; sources de données |
| Workflow pages villes | `Emilienzabu/CarburantRadar` | `.github/workflows/generate-city-pages.yml` | `main` | `c066bde` | début lu le 2026-11-06 (clone) ; il commite l'état du générateur dans `main`, donc `main` avance chaque jour | Lance le générateur SEO | Lancement soumis à autorisation explicite (D-009, D-016) |
| Workflow vidéo du jour | `Emilienzabu/CarburantRadar` | `.github/workflows/video-du-jour.yml` | `main` | `c066bde` | lu le 2026-11-06 (clone en lecture seule ; le connecteur reste bloqué sur `.github/`) | Déclenchements `40 6 * * *` et `40 16 * * *` UTC et manuel ; appelle `video/generate_video.py` ; secret `VIDEO_API_KEY` ; artefact `video-du-jour` conservé 7 jours (sans date ni créneau dans le nom) | Modification non possible par le connecteur : la garde astuce est donc implémentée en Python (PR #33) |
| Générateur vidéo | `Emilienzabu/CarburantRadar` | `video/generate_video.py` (+ `audio.py`, `donnees.py`, `rendu.py`, `musique.py`) | `main` | `c066bde` | `generate_video.py`, `donnees.py` et `audio.py` lus le 2026-11-06 ; `rendu.py` lu en partie et exécuté (rendu réel en sandbox) ; `musique.py` non lu | Vidéos 9:16 et publication | `VIDEO_API_KEY`, Worker `video-automation`, voix `edge-tts` ; **filtre géographique ignoré par l'API (audit E0)** ; PR #33 (garde astuce, branche `securite-astuce-publication`, non fusionnée) |
| Worker `carburant-proxy` | Cloudflare (hors dépôt) | sans objet | sans objet | sans objet | code non relu | Proxy API, comptes, alertes, `/es`, `/it`, `/track`, `/admin/*` | Voir [worker_proxy.md](worker_proxy.md) ; protection `/admin/*` À CONFIRMER |
| Worker `video-automation` | Cloudflare (hors dépôt) | sans objet | sans objet | sans objet | code non lu ; contrat d'appel (`POST /api/upload`, en-tête `Authorization: Bearer`, champs `profile`, `title`, `description`, `caption`, fichier `video`) lu dans `generate_video.py` le 2026-11-06 | Réception des vidéos, publication YouTube/Instagram | Jetons OAuth, quotas, portées des autorisations, liaisons KV/R2/D1 : À CONFIRMER ; code à fournir par Émilien |
| Worker `carburant-mcp` | Cloudflare (hors dépôt) | sans objet | sans objet | sans objet | code relu et modifié (v1.1.0) le 2026-11-04 | Connecteur MCP de Claude vers les dépôts GitHub | Secret dans l'URL ; liste blanche de 2 dépôts ; ne pas modifier sans autorisation (D-013) |
