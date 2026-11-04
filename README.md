# CarburantRadar-Workspace

Dépôt **documentaire privé** du projet CarburantRadar. Il sert de mémoire partagée entre **Claude** et **ChatGPT** : contexte, audits, décisions, avancement.

- Ce dépôt = documentation de référence. Il ne contient **aucun code de production**.
- Le projet de production est un autre dépôt : `Emilienzabu/CarburantRadar` (GitHub Pages). On n'y touche jamais depuis ce workspace.
- Dernière mise à jour de la structure : 2026-11-04.

## Démarrer une session (Claude ou ChatGPT)

Lire dans cet ordre :

1. [README.md](README.md) (ce fichier)
2. [CONTEXTE_GLOBAL.md](CONTEXTE_GLOBAL.md)
3. [AVANCEMENT.md](AVANCEMENT.md)
4. [DECISIONS.md](DECISIONS.md)
5. [REGLES_DE_TRAVAIL.md](REGLES_DE_TRAVAIL.md)
6. Puis les fichiers propres à la tâche (voir l'arborescence plus bas et [MANIFESTE.md](MANIFESTE.md)).

## Terminer une session

1. Mettre à jour [AVANCEMENT.md](AVANCEMENT.md).
2. Ajouter un compte rendu dans [journal/](journal/README.md) (modèle : [modeles/compte_rendu_session.md](modeles/compte_rendu_session.md)).
3. Mettre à jour [CHANGELOG.md](CHANGELOG.md) seulement si des modifications documentaires ou techniques ont réellement eu lieu.
4. Modifier [DECISIONS.md](DECISIONS.md) **uniquement** si une décision a été explicitement acceptée par Émilien.
5. Conserver les informations non vérifiées avec leur statut (ne jamais les « promouvoir » en faits).

## Statuts de fiabilité (obligatoires)

Chaque information importante porte un statut : VÉRIFIÉ, RAPPORTÉ PAR L'UTILISATEUR, À CONFIRMER, HYPOTHÈSE, PROPOSITION, ACCEPTÉ, EN COURS, TERMINÉ, BLOQUÉ. Définitions et règles : [REGLES_DE_TRAVAIL.md](REGLES_DE_TRAVAIL.md).

## Comment Claude et ChatGPT utilisent ce dépôt

**Claude**
- Accès via le connecteur MCP `carburant-mcp` (Worker Cloudflare, version 1.1.0) avec le paramètre `repo` = `CarburantRadar-Workspace`.
- Lecture : `get_file`. Écriture : jamais directement sur `main` ; Claude crée une branche, pousse un commit, ouvre une pull request. **Émilien fusionne.**
- Le connecteur refuse l'accès au dossier `.github/` (protection volontaire du Worker).

**ChatGPT**
- Lit le dépôt (connecteur GitHub de ChatGPT ou fichiers collés par Émilien). À CONFIRMER : la capacité d'écriture directe de ChatGPT sur ce dépôt privé.
- Si ChatGPT n'écrit pas directement : il produit le texte de mise à jour, Émilien le colle dans une conversation Claude, qui prépare la pull request.

**Dans les deux cas** : ne jamais écrire de mot de passe, token, clé API ou donnée personnelle ici ([SECURITE_ET_SECRETS.md](SECURITE_ET_SECRETS.md)).

## Arborescence

| Dossier / fichier | Contenu |
|---|---|
| [CONTEXTE_GLOBAL.md](CONTEXTE_GLOBAL.md) | Présentation, objectifs, dépôts, contraintes |
| [AVANCEMENT.md](AVANCEMENT.md) | État du travail (EN COURS, TERMINÉ, BLOQUÉ) |
| [DECISIONS.md](DECISIONS.md) | Décisions explicitement acceptées |
| [REGLES_DE_TRAVAIL.md](REGLES_DE_TRAVAIL.md) | Règles permanentes, statuts |
| [INVENTAIRE_TECHNIQUE.md](INVENTAIRE_TECHNIQUE.md) | Composants techniques et leur niveau de certitude |
| [SECURITE_ET_SECRETS.md](SECURITE_ET_SECRETS.md) | Où vivent les secrets (sans jamais les écrire) |
| [CHANGELOG.md](CHANGELOG.md) | Historique des modifications |
| [MANIFESTE.md](MANIFESTE.md) | Liste commentée des 32 fichiers |
| [codes/](codes/README.md) | Notes sur le code (Python, Workers, Actions) |
| [audits/](audits/README.md) | Audits techniques |
| [strategie/](strategie/README.md) | Acquisition, éditorial, mesure |
| [produit/](produit/README.md) | Fonctionnalités, données, idées |
| [journal/](journal/README.md) | Comptes rendus de sessions |
| [modeles/](modeles/compte_rendu_session.md) | Modèles de fiches |
