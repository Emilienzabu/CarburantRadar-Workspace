# Audit du générateur vidéo

Base : lecture **statique** du dossier `video/` du dépôt de production (2026-11-04) : `generate_video.py`, `audio.py`, `donnees.py`, `rendu.py`, `requirements.txt` en entier, et `musique.py` en partie (3 500 caractères sur 8 179). Rien n'a été exécuté : aucune vidéo générée ou publiée, aucun appel à l'API de prix, aucun test de la voix. Ici, VÉRIFIÉ veut dire « lu dans le code », pas « testé ». Fonctionnement détaillé : [../codes/worker_video.md](../codes/worker_video.md).

## Ce que fait le code (VÉRIFIÉ)

- Chaîne complète : prix officiels, scènes de texte, voix, musique générée par code, rendu 1080x1920 à 30 images/s, envoi au Worker.
- Garde-fous : pas de publication sans voix, sans clé, sans ville exploitable (minimum 8 stations avec un prix récent) ; repli classement vers ville, carburant rare vers gazole.
- Contrôle sans publier : `--demo` (données factices) et `--png` (images de contrôle).

## Problèmes constatés dans le code (VÉRIFIÉ, impact à mesurer)

| N° | Constat | Statut de l'impact |
|---|---|---|
| 1 | La scène des 3 moins chères affiche « Prix officiels · mis à jour aujourd'hui », alors que le code accepte des prix jusqu'à 5 jours (`MAX_AGE_JOURS = 5`). Le texte peut donc être inexact. | Texte inexact possible : VÉRIFIÉ ; fréquence réelle : À CONFIRMER |
| 2 | Les textes (voix, sous-titre, titre, description) écrivent « À Le Havre » et « à Le Mans » : l'article n'est pas géré. Concerne 2 des 34 villes. | VÉRIFIÉ |
| 3 | Le lien publié est `https://carburantradar.fr` (racine), sans UTM et sans page ville ; sur Instagram, la légende dit « lien en bio ». | Attribution impossible par l'URL : HYPOTHÈSE |
| 4 | La publication compte comme réussie si YouTube **ou** Instagram réussit ; pas de nouvelle tentative. Le contenu est déterministe (formule date et créneau) : relancer le même créneau republie le même format. | Doublon ou publication d'une seule plateforme : HYPOTHÈSE |
| 5 | `requirements.txt` (pillow, numpy, requests, edge-tts) sans versions ; `ffmpeg` est appelé en ligne de commande mais n'est pas dans les dépendances Python. | Rupture après mise à jour d'une dépendance : HYPOTHÈSE ; ffmpeg présent sur l'exécuteur : À CONFIRMER |
| 6 | Le classement compare des moyennes calculées dans des rayons différents (Paris 6,5 km, Marseille 9 km, Nice et Lyon 7 à 8 km, etc.). | Comparaison un peu biaisée : HYPOTHÈSE |
| 7 | L'écart annoncé sur un plein de 50 L est (prix max moins prix min) x 50 : un prix extrême (station d'autoroute, erreur de saisie) gonfle le chiffre d'accroche. | Chiffre exagéré : HYPOTHÈSE |
| 8 | Si la police Poppins ne se télécharge pas et qu'aucune police de secours n'existe sur la machine, le rendu s'arrête avec une erreur. | Cas limite : À CONFIRMER selon l'exécuteur |

Points mineurs (VÉRIFIÉ) : le plein de 50 L est écrit en dur à deux endroits (`LITRES` et le texte « 50 L » du rendu) ; la voix arrondit les prix au centime alors que l'écran affiche trois décimales ; le format astuce n'a pas de sous-titre hors scène finale (le texte reste affiché à l'écran).

## Voix, musique, rythme (VÉRIFIÉ code)

- Voix : bibliothèque `edge-tts`, voix `fr-FR-RemyMultilingualNeural`, secours `fr-FR-HenriNeural`, 3 essais par scène. Disponibilité et conditions du service : À CONFIRMER (HYPOTHÈSE de risque : service non garanti).
- Musique générée par code (aucun fichier audio), 6 styles qui changent à chaque publication ; voix au-dessus, musique baissée pendant la parole ; normalisation loudnorm à -14 LUFS.
- Durées minimales des scènes : ville 22,8 s, classement 17,8 s, astuce 20,6 s ; la durée réelle suit la voix (non mesurée).
- Planning (poids dans le code) : format ville 50 %, classement 30 %, astuce 20 % ; carburants (ville) gazole 17, E10 15, SP98 5, E85 2, GPL 1 ; 34 villes pondérées de 1 à 6 ; 7 astuces seulement.

## À confirmer (non lu)

- Fin de `musique.py` (lignes après 3 500 caractères).
- Worker `video-automation`, workflow de publication, résultat de la cellule B ([../codes/cellules_python.md](../codes/cellules_python.md)).
- Rendu réel : zones masquées par l'interface YouTube Shorts et Instagram (les sous-titres sont placés vers y = 1340 à 1400 sur 1920 : HYPOTHÈSE de chevauchement, à voir sur un téléphone).

## Pistes d'amélioration (PROPOSITION, rien n'est décidé ; la règle D-009 impose un plan validé avant toute modification)

- Lien : ajouter des UTM par vidéo (source, support, format, ville, numéro de publication) et pointer vers la page ville SEO correspondante quand elle existe (correspondance des 34 slugs avec les pages du site : À CONFIRMER). Pour Instagram, le lien du profil porte l'UTM.
- Corriger le texte de fraîcheur (« mis à jour récemment » ou limite à 1 jour) et l'article des villes (« au Havre », « au Mans »).
- Limiter l'influence des prix extrêmes dans le chiffre d'accroche ; harmoniser les rayons du classement.
- Rendre la publication reprenable sans doublon (mémoriser ce qui est déjà publié) et épingler les dépendances.
- Élargir la variété : plus d'astuces, plus de villes, variantes d'accroche testées par format ([../strategie/mesure_performance.md](../strategie/mesure_performance.md)).
- Contrôle visuel automatique avec `--png` avant publication.

La liste d'améliorations des conversations précédentes n'est pas disponible dans cette session : À COMPLÉTER avec Émilien.
