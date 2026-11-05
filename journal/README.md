# Journal

**Un fichier par jour** de travail, nommé `AAAA-MM-JJ.md`, avec **une section par assistant et par session**.

## Format d'un fichier journal

- Titre : `# Journal du AAAA-MM-JJ`.
- Une section `## [Claude] — titre de la session` ou `## [ChatGPT] — titre de la session`, au format en 11 sections de [../modeles/compte_rendu_session.md](../modeles/compte_rendu_session.md) (partie 1).
- Plusieurs sessions le même jour : plusieurs sections dans le même fichier, sans toucher à celles de l'autre assistant.
- **Paquet de transfert ChatGPT → Claude** : Claude le place dans une section `[ChatGPT]` en deux temps. D'abord un **compte rendu synthétique en 11 sections**, puis, sous le sous-titre `### Paquet de transfert reçu (intégral)`, le **paquet conservé intégralement**, tel que reçu (rien n'est résumé, supprimé ni reformulé : preuves, hypothèses, extraits de code, propositions non validées, prochaines actions), dans un bloc à quatre accents graves. L'en-tête du paquet reste tel que reçu ; le statut courant est suivi dans [../AVANCEMENT.md](../AVANCEMENT.md) et [../CHANGELOG.md](../CHANGELOG.md) ([../REGLES_DE_TRAVAIL.md](../REGLES_DE_TRAVAIL.md), sections 3 et 8).
- Un journal ne se réécrit pas : une correction passe par une nouvelle entrée.
- Le fichier du 2026-11-04 a été commencé avant ce format ; son contenu d'origine est conservé tel quel (c'est une session `[Claude]`) et la session suivante du jour y est ajoutée à la suite.

## Index (du plus récent au plus ancien)

La **première ligne** est le dernier journal à lire au début d'une conversation.

| Date | Résumé |
|---|---|
| [2026-11-05](2026-11-05.md) | [ChatGPT] Paquet de transfert (plan de corrections et d'améliorations) reçu et intégré par Claude, avec vérification contre le code vidéo lu (branche `integration-paquet-chatgpt-2026-11-05`) |
| [2026-11-04](2026-11-04.md) | [Claude] Création du workspace, connecteur multi-dépôts ; [Claude] protocole de mémoire partagée (branche `protocole-memoire`) |

Après chaque session : ajouter ou compléter la ligne correspondante (en haut du tableau) et mettre à jour [../AVANCEMENT.md](../AVANCEMENT.md) si le travail le concerne.
