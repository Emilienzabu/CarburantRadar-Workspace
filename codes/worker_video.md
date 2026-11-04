# Génération et publication vidéo

Source : lecture statique de `video/` (2026-11-04), voir [../audits/audit_videos.md](../audits/audit_videos.md). Le Worker `video-automation` et `musique.py` (fin) n'ont pas été lus : À CONFIRMER.

## Fichiers de `video/` (VÉRIFIÉ)

| Fichier | Rôle |
|---|---|
| `generate_video.py` | Orchestration, options en ligne de commande, envoi au Worker |
| `donnees.py` | Prix officiels, choix du contenu, calculs, textes, titres et descriptions |
| `audio.py` | Voix (`edge-tts`), durée des scènes, mixage |
| `musique.py` | Musique générée par code (6 styles, graine par publication) |
| `rendu.py` | Images (Pillow) et encodage (ffmpeg) |
| `requirements.txt` | pillow, numpy, requests, edge-tts (sans versions) |

Programme externe requis : `ffmpeg` (non listé dans `requirements.txt`).

## Parcours d'une exécution (VÉRIFIÉ)

1. Créneau : matin avant 13 h (Paris), sinon soir ; numéro de publication `k` = jour x 2 (+1 le soir).
2. Plan : format, carburant, ville tirés de façon déterministe selon des poids.
3. Données : API officielle `prix-des-carburants-en-france-flux-instantane-v2` (filtre `geofilter.distance` lat, lon, rayon en mètres, pages de 100), prix entre 0,8 et 3,5 €, âge maximum 5 jours, doublons d'adresse retirés, 8 stations minimum.
4. Scènes de texte, puis voix (secours Henri), durée de chaque scène calée sur la voix.
5. Mixage (musique baissée sous la voix, loudnorm -14 LUFS), rendu 1080x1920, 30 images/s, x264 crf 20.
6. Si `--publier` : envoi au Worker (voir ci-dessous).

## Formats

| Format | Poids | Scènes | Contenu |
|---|---|---|---|
| ville | 5 | accroche, top 3, économie, appel à l'action | Écart sur un plein de 50 L, 3 moins chères, économie par rapport à la moyenne |
| classement | 3 | accroche, classement, appel à l'action | 11 grandes villes possibles (au moins 5 exploitables), top 5 des moyennes |
| astuce | 2 | titre, 3 conseils, appel à l'action | 7 astuces fixes sans chiffres |

## Publication (VÉRIFIÉ)

- `POST` multipart vers `https://video-automation.emilienzabukovec09.workers.dev/api/upload`, en-tête `Authorization: Bearer <VIDEO_API_KEY>`.
- Champs : `profile=carburant`, `title` (100 caractères max), `description` (600 max, avec `#Shorts` et le lien `https://carburantradar.fr`), `caption` (légende Instagram, « lien en bio »), fichier `video`.
- Réponse lue : blocs `youtube` et `instagram` ; succès si l'un des deux réussit.

## Worker `video-automation`

Contrat d'appel connu (ci-dessus). Code, jetons OAuth YouTube et Instagram, quotas, journalisation : À CONFIRMER. Lien avec le SaaS de publication vidéo d'Émilien : HYPOTHÈSE.

## Commandes documentées dans le code

- `python video/generate_video.py --demo --format classement` : essai sans réseau pour les prix.
- `python video/generate_video.py` : contenu prévu pour le créneau, sans publier.
- `python video/generate_video.py --publier` : publie (clé dans `VIDEO_API_KEY`).
- `python video/generate_video.py --format ville --ville marseille --carburant gazole`.

Selon la règle D-009 ([../DECISIONS.md](../DECISIONS.md)), aucune de ces commandes n'est lancée sans autorisation explicite d'Émilien.
