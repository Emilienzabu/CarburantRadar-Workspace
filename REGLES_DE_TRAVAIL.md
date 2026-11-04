# Règles de travail

Règles permanentes pour Claude et ChatGPT. Source : consignes de mission d'Émilien du 2026-11-04 (RAPPORTÉ PAR L'UTILISATEUR).

## Statuts de fiabilité

| Statut | Sens |
|---|---|
| VÉRIFIÉ | Confirmé directement dans le code ou par un test réellement exécuté |
| RAPPORTÉ PAR L'UTILISATEUR | Information donnée par Émilien |
| À CONFIRMER | Information ancienne ou non vérifiée |
| HYPOTHÈSE | Explication possible, non démontrée |
| PROPOSITION | Amélioration suggérée, pas encore décidée |
| ACCEPTÉ | Décision explicitement validée par Émilien |
| EN COURS | Travail commencé |
| TERMINÉ | Travail réellement effectué |
| BLOQUÉ | Problème empêchant d'avancer |

Interdits : présenter une hypothèse comme un fait ; prétendre avoir testé ce qui ne l'a pas été ; transformer une proposition en décision sans accord.

## Séparation des dépôts

- `CarburantRadar-Workspace` (ce dépôt) : documentation uniquement.
- `CarburantRadar` : production. Aucune modification de code, aucun déploiement, aucune automatisation lancée, sans autorisation explicite d'Émilien pour la tâche concernée.

## Interdits permanents

- Ne modifier aucun secret, token, compte OAuth ou configuration Cloudflare.
- Ne dépenser aucun argent.
- Ne jamais écrire de mot de passe, token, clé API ou donnée personnelle dans ce dépôt (voir [SECURITE_ET_SECRETS.md](SECURITE_ET_SECRETS.md)).
- Garder le dépôt privé.
- Ne supprimer aucun fichier sans nécessité et sans en informer Émilien.

## Écriture dans le workspace

- Claude : branche, un commit cohérent, pull request ; Émilien fusionne. Jamais d'écriture directe sur `main`.
- Un commit par session de travail plutôt que de nombreux petits commits.
- Liens relatifs entre fichiers ; pas de répétitions inutiles (renvoyer vers le fichier de référence).

## Début et fin de session

Voir [README.md](README.md). Modèles : [modeles/](modeles/compte_rendu_session.md).

## Style

- Réponses concises, orientées action, adaptées à la situation d'Émilien (RAPPORTÉ PAR L'UTILISATEUR).
- Pour les modifications d'app : fichiers complets, pas de diffs partiels.
- Pour la rédaction de documents : discuter et ajuster avant de régénérer un fichier final.
