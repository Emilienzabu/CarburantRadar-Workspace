# Manifeste

Objectifs et principes du projet de mémoire partagée, puis liste commentée des 32 fichiers (état au 2026-11-04). Quand un fichier est ajouté ou supprimé, mettre à jour cette liste et le [CHANGELOG.md](CHANGELOG.md).

## Objectifs

- Faire de ce dépôt la **mémoire centrale et permanente** de CarburantRadar, commune à ChatGPT et à Claude.
- Qu'une nouvelle conversation reprenne le projet sans qu'Émilien ait à tout réexpliquer.
- Que ChatGPT puisse reprendre un travail de Claude, et inversement, sans refaire les analyses déjà effectuées.
- Conserver les codes de référence, décisions, audits, découvertes et travaux en cours.
- Soutenir les objectifs du produit : trouver les stations les moins chères à partir de données officielles, croissance des utilisateurs d'abord ([CONTEXTE_GLOBAL.md](CONTEXTE_GLOBAL.md), [DECISIONS.md](DECISIONS.md) D-002).

## Principes

- **Honnêteté des statuts** : une hypothèse n'est pas un fait, une proposition n'est pas une décision, une tâche n'est TERMINÉE que si le résultat est obtenu et vérifié ([REGLES_DE_TRAVAIL.md](REGLES_DE_TRAVAIL.md)).
- **Décision = accord explicite d'Émilien**, consigné dans [DECISIONS.md](DECISIONS.md).
- **Données réelles, rien d'inventé** : chaque information porte sa preuve ou son statut.
- **Confiance avant tout** : aucune station ne peut payer pour être mieux classée (D-004).
- **Sécurité** : aucun secret ni donnée personnelle ici, dépôt privé, production séparée ([SECURITE_ET_SECRETS.md](SECURITE_ET_SECRETS.md)).
- **Travail traçable** : branche et pull request fusionnée par Émilien, journal par session, un fichier de référence par sujet (pas de copies).
- **Coordination sans conflit** : ne pas écraser le travail de l'autre assistant ; un paquet n'est INTÉGRÉ qu'une fois présent dans `main`.

## Racine (9)

- [README.md](README.md) : mode d'emploi du workspace et ordre de lecture
- [CONTEXTE_GLOBAL.md](CONTEXTE_GLOBAL.md) : projet, dépôts, priorités
- [AVANCEMENT.md](AVANCEMENT.md) : EN COURS, TERMINÉ, BLOQUÉ, propositions et paquets en attente
- [DECISIONS.md](DECISIONS.md) : décisions ACCEPTÉES
- [REGLES_DE_TRAVAIL.md](REGLES_DE_TRAVAIL.md) : protocole commun, statuts
- [INVENTAIRE_TECHNIQUE.md](INVENTAIRE_TECHNIQUE.md) : composants techniques
- [SECURITE_ET_SECRETS.md](SECURITE_ET_SECRETS.md) : gestion des secrets, règles de sécurité
- [CHANGELOG.md](CHANGELOG.md) : historique des modifications
- [MANIFESTE.md](MANIFESTE.md) : ce fichier

## codes/ (5)

- [codes/README.md](codes/README.md) (index et registre des versions), [codes/cellules_python.md](codes/cellules_python.md), [codes/worker_proxy.md](codes/worker_proxy.md), [codes/worker_video.md](codes/worker_video.md), [codes/github_actions.md](codes/github_actions.md)

## audits/ (5)

- [audits/README.md](audits/README.md), [audits/audit_application.md](audits/audit_application.md), [audits/audit_videos.md](audits/audit_videos.md), [audits/securite_confidentialite.md](audits/securite_confidentialite.md), [audits/audit_international.md](audits/audit_international.md)

## strategie/ (4)

- [strategie/README.md](strategie/README.md), [strategie/acquisition_utilisateurs.md](strategie/acquisition_utilisateurs.md), [strategie/strategie_editoriale.md](strategie/strategie_editoriale.md), [strategie/mesure_performance.md](strategie/mesure_performance.md)

## produit/ (4)

- [produit/README.md](produit/README.md), [produit/fonctionnalites.md](produit/fonctionnalites.md), [produit/donnees_et_sources.md](produit/donnees_et_sources.md), [produit/idees_et_ameliorations.md](produit/idees_et_ameliorations.md)

## journal/ (2)

- [journal/README.md](journal/README.md) (règles et index), [journal/2026-11-04.md](journal/2026-11-04.md)

## modeles/ (3)

- [modeles/compte_rendu_session.md](modeles/compte_rendu_session.md) (compte rendu en 11 sections et paquet de transfert ChatGPT → Claude), [modeles/fiche_idee.md](modeles/fiche_idee.md), [modeles/fiche_anomalie.md](modeles/fiche_anomalie.md)
