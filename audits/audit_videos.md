# Audit du générateur vidéo

Base : lecture statique de `video/generate_video.py` (2026-11-04). Les autres modules n'ont pas été lus et **aucune vidéo n'a été générée ni publiée par Claude** pendant cette mission. Description du fonctionnement : [../codes/worker_video.md](../codes/worker_video.md).

## Constats VÉRIFIÉS (code)

- Chaîne complète : données réelles, scènes de texte, voix, musique, rendu 9:16, envoi au Worker.
- Garde-fous de qualité présents : pas de publication sans voix, sans clé, ou sans ville exploitable ; repli du classement vers une ville et du carburant vers le gazole.
- Mode `--demo` et mode `--png` permettent de contrôler le rendu sans publier.
- Le contenu alterne trois formats ; deux publications par jour.

## Points à clarifier (À CONFIRMER)

- Service de synthèse vocale utilisé par `audio.py` et ses limites (quota, disponibilité, coût).
- Contenu de `donnees.textes_publication` : présence d'un lien de destination et d'un suivi UTM dans la description (objectif de la mission : visites, pas vues).
- Planification et déclencheur du workflow de publication ([../codes/github_actions.md](../codes/github_actions.md)).
- Résultat de la cellule B (génération `--demo` + test TTS) : [../codes/cellules_python.md](../codes/cellules_python.md).

## Hypothèses de risque (HYPOTHÈSE)

- Dépendance au téléchargement des polices à chaque exécution : repli prévu, mais rendu visuel différent si échec.
- Une publication partielle (une seule plateforme réussie) est comptée comme succès : possible écart entre YouTube et Instagram.

## Améliorations graphiques et qualitatives (PROPOSITION, non décidées)

- Accroche forte dans les 2 premières secondes ; sous-titres lisibles ; appel à l'action visible en fin de vidéo vers le site.
- Variété visuelle entre les trois formats ; vérification automatique du rendu (images de contrôle `--png`) avant publication.
- Mesure par format pour garder ce qui amène des visites : voir [../strategie/mesure_performance.md](../strategie/mesure_performance.md).

La liste d'améliorations discutée dans les sessions précédentes n'était pas disponible pendant l'écriture de ce fichier : À COMPLÉTER.
