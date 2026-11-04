# Génération et publication vidéo

Ce qui est **VÉRIFIÉ** provient de la lecture de `video/generate_video.py` (dépôt de production, 2026-11-04). Le code de `audio.py`, `donnees.py`, `rendu.py`, `musique.py` et du Worker n'a pas été lu : À CONFIRMER.

## Fichiers du dossier `video/`

`generate_video.py` (orchestration), `audio.py` (voix), `donnees.py` (données et textes), `rendu.py` (image), `musique.py` (musique), `requirements.txt`, `.gitignore`. VÉRIFIÉ (listing).

## Fonctionnement de `generate_video.py` (VÉRIFIÉ)

- Produit une vidéo verticale 9:16 avec voix d'homme et musique à partir de prix réels.
- Deux créneaux par jour, « matin » (avant 13 h, heure de Paris) et « soir » ; le numéro de publication `k` dépend de la date et du créneau.
- Trois formats : `ville` (prix d'une ville pour un carburant, top 3, économie sur un plein), `classement` (villes les moins chères parmi les plus grandes), `astuce` (conseil général sans chiffres).
- Repli : si le classement est impossible, bascule sur une ville ; si le carburant demandé est introuvable, bascule sur le gazole ; si aucune ville n'est exploitable, rien n'est publié.
- Polices Poppins téléchargées depuis le dépôt `google/fonts` ; police de secours si le téléchargement échoue.
- Options : `--demo`, `--format`, `--creneau`, `--ville`, `--carburant`, `--publier`, `--sortie`, `--voix`, `--png` (images de contrôle).
- Publication (`--publier`) : envoi `POST` multipart vers `https://video-automation.emilienzabukovec09.workers.dev/api/upload` avec en-tête `Authorization: Bearer <VIDEO_API_KEY>` et champs `profile=carburant`, `title`, `description`, `caption`, fichier `video`.
- Garde-fous : refuse de publier si la voix est indisponible ou si `VIDEO_API_KEY` manque ; échec si la publication échoue sur les deux plateformes (YouTube et Instagram).

## Worker `video-automation`

Reçoit la vidéo et publie sur YouTube et Instagram (réponse JSON avec blocs `youtube` et `instagram`). VÉRIFIÉ pour le contrat d'appel ; code, jetons OAuth et quotas : À CONFIRMER. Lien éventuel avec le SaaS de publication vidéo d'Émilien : HYPOTHÈSE.
