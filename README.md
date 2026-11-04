# CarburantRadar-Workspace

Dépôt **documentaire privé** du projet CarburantRadar. Il sert de **mémoire centrale et permanente**, partagée entre **Claude** et **ChatGPT** : contexte, décisions, audits, avancement, références de code.

- Ce dépôt = documentation de référence. Il ne contient **aucun code de production**.
- Le projet de production est un autre dépôt : `Emilienzabu/CarburantRadar` (GitHub Pages). Aucune modification de ce dépôt depuis ici sans autorisation explicite d'Émilien pour la tâche concernée ([REGLES_DE_TRAVAIL.md](REGLES_DE_TRAVAIL.md)).
- Dernière mise à jour de la structure : 2026-11-04 (protocole de mémoire partagée, D-012).

## Démarrer une conversation (Claude ou ChatGPT)

Lire dans cet ordre :

1. [README.md](README.md) (ce fichier)
2. [REGLES_DE_TRAVAIL.md](REGLES_DE_TRAVAIL.md)
3. [CONTEXTE_GLOBAL.md](CONTEXTE_GLOBAL.md)
4. [AVANCEMENT.md](AVANCEMENT.md)
5. [DECISIONS.md](DECISIONS.md)
6. Le dernier journal : première ligne du tableau de [journal/README.md](journal/README.md)
7. Puis les fichiers utiles à la tâche (arborescence plus bas, [MANIFESTE.md](MANIFESTE.md))

Avant d'agir, identifier : le contexte actuel ; les travaux déjà effectués ; les tâches en cours ; les problèmes non résolus ; les propositions en attente ; les dernières modifications du dépôt ; la prochaine action logique.

Règles de reprise :

- Ne pas demander à Émilien de renvoyer une information déjà présente ici et accessible.
- Si un fichier ou le dépôt est inaccessible, le dire honnêtement ; ne jamais prétendre l'avoir lu.
- Travailler sur les versions réelles et actuelles du code, pas sur d'anciennes copies.

## Terminer une session importante

1. Ajouter un compte rendu dans `journal/AAAA-MM-JJ.md` : une section `[Claude]` ou `[ChatGPT]` (modèle en 11 sections : [modeles/compte_rendu_session.md](modeles/compte_rendu_session.md)) et la ligne correspondante dans [journal/README.md](journal/README.md).
2. Mettre à jour **seulement les fichiers concernés** par le travail : [AVANCEMENT.md](AVANCEMENT.md), [CHANGELOG.md](CHANGELOG.md) (modifications réellement effectuées), [DECISIONS.md](DECISIONS.md) (**uniquement** une décision explicitement acceptée par Émilien), fichiers d'audit, [CONTEXTE_GLOBAL.md](CONTEXTE_GLOBAL.md) (connaissance durable modifiée), [INVENTAIRE_TECHNIQUE.md](INVENTAIRE_TECHNIQUE.md) (architecture modifiée), registre des versions de [codes/README.md](codes/README.md).
3. Ne pas actualiser artificiellement un fichier que le travail ne concerne pas.
4. Conserver les informations non vérifiées avec leur statut (ne jamais les « promouvoir » en faits).

## Statuts

- Fiabilité : VÉRIFIÉ, RAPPORTÉ PAR L'UTILISATEUR, À CONFIRMER, HYPOTHÈSE, PROPOSITION, ACCEPTÉ, EN COURS, TERMINÉ, BLOQUÉ.
- Transmission d'un paquet ChatGPT → Claude : EN ATTENTE DE TRANSMISSION, EN ATTENTE D'INTÉGRATION, INTÉGRÉ.

Définitions et règles de promotion : [REGLES_DE_TRAVAIL.md](REGLES_DE_TRAVAIL.md).

## Comment Claude et ChatGPT utilisent ce dépôt

**Claude**
- Accès via le connecteur MCP `carburant-mcp` (Worker Cloudflare, version 1.1.0) avec le paramètre `repo` = `CarburantRadar-Workspace`.
- Lecture : `get_file`. Écriture : jamais directement sur `main` ; Claude crée une branche, pousse un commit, ouvre une pull request. **Émilien fusionne.**
- Le connecteur refuse l'accès au dossier `.github/` (protection volontaire du Worker). Il n'offre pas d'outil pour lister branches, PR ou commits.

**ChatGPT**
- Lecture : connecteur GitHub de ChatGPT ou fichiers collés par Émilien. Lecture réelle du Workspace par le connecteur : À CONFIRMER (test à faire).
- Écriture directe sur ce dépôt : À CONFIRMER, ne pas la supposer possible.
- Transmission : ChatGPT prépare un **paquet de transfert** ; Émilien le copie dans une conversation Claude ; Claude l'intègre par branche et PR. Format et fonctionnement : [modeles/compte_rendu_session.md](modeles/compte_rendu_session.md) et [REGLES_DE_TRAVAIL.md](REGLES_DE_TRAVAIL.md) (sections 3 et 8).

**Dans tous les cas** : ne jamais écrire de mot de passe, token, clé API ou donnée personnelle ici ([SECURITE_ET_SECRETS.md](SECURITE_ET_SECRETS.md)).

## Arborescence

| Dossier / fichier | Contenu |
|---|---|
| [CONTEXTE_GLOBAL.md](CONTEXTE_GLOBAL.md) | Présentation, objectifs, dépôts, contraintes |
| [AVANCEMENT.md](AVANCEMENT.md) | État du travail (EN COURS, TERMINÉ, BLOQUÉ), propositions et paquets en attente |
| [DECISIONS.md](DECISIONS.md) | Décisions explicitement acceptées |
| [REGLES_DE_TRAVAIL.md](REGLES_DE_TRAVAIL.md) | Protocole commun, statuts |
| [INVENTAIRE_TECHNIQUE.md](INVENTAIRE_TECHNIQUE.md) | Composants techniques et leur niveau de certitude |
| [SECURITE_ET_SECRETS.md](SECURITE_ET_SECRETS.md) | Où vivent les secrets (sans jamais les écrire), règles de sécurité |
| [CHANGELOG.md](CHANGELOG.md) | Historique des modifications |
| [MANIFESTE.md](MANIFESTE.md) | Objectifs et principes, liste commentée des 32 fichiers |
| [codes/](codes/README.md) | Notes sur le code et registre des versions |
| [audits/](audits/README.md) | Audits techniques |
| [strategie/](strategie/README.md) | Acquisition, éditorial, mesure |
| [produit/](produit/README.md) | Fonctionnalités, données, idées |
| [journal/](journal/README.md) | Comptes rendus de sessions (un fichier par jour) |
| [modeles/](modeles/compte_rendu_session.md) | Modèles : compte rendu, paquet de transfert, anomalie, idée |
