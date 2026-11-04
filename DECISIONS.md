# Décisions

Ne contient **que** des décisions explicitement acceptées par Émilien. Une proposition n'entre ici qu'avec son accord (voir [produit/idees_et_ameliorations.md](produit/idees_et_ameliorations.md) et la section « Propositions en attente » de [AVANCEMENT.md](AVANCEMENT.md) pour les idées non décidées).

Format : identifiant, date, décision, statut, source.

| ID | Date | Décision | Statut | Source |
|---|---|---|---|---|
| D-001 | ancienne | Architecture multi-pays : un dossier et un `index.html` par pays (pas de système i18n dynamique), sélecteur de pays à la racine qui mémorise le choix | ACCEPTÉ | RAPPORTÉ PAR L'UTILISATEUR |
| D-002 | ancienne | Priorité à la croissance des utilisateurs, monétisation ensuite | ACCEPTÉ | RAPPORTÉ PAR L'UTILISATEUR |
| D-003 | 2026-10-08 | Pas de publicités tant qu'il n'y a pas d'utilisateurs récurrents | ACCEPTÉ | RAPPORTÉ PAR L'UTILISATEUR |
| D-004 | ancienne | Priorité absolue : garder la confiance. Une station ne doit jamais pouvoir payer pour être mieux classée | ACCEPTÉ | RAPPORTÉ PAR L'UTILISATEUR |
| D-005 | 2026-09-30 | Chantier SEO : générer automatiquement toutes les communes françaises avec assez de stations | ACCEPTÉ | RAPPORTÉ PAR L'UTILISATEUR |
| D-006 | 2026-10-06 | Traiter d'abord le cache du dernier jeu de données de l'API espagnole, avant l'erreur de sitemap et le domaine | ACCEPTÉ | RAPPORTÉ PAR L'UTILISATEUR |
| D-007 | ancienne | Décisions de périmètre : option 50 km abandonnée, pas de récupération de mot de passe, pas de bannière RGPD avant l'activation des pubs | ACCEPTÉ ; à re-confirmer car la note date de septembre | RAPPORTÉ PAR L'UTILISATEUR |
| D-008 | ancienne | Refus de Claude Code (payant) ; solution gratuite et automatisée souhaitée pour que Claude modifie les dépôts | ACCEPTÉ | RAPPORTÉ PAR L'UTILISATEUR |
| D-009 | 2026-11-04 | Mission vidéo : audit puis plan validé avant toute modification ; aucun commit, push, changement de workflow, secret, variable Cloudflare, token ou publication sans autorisation explicite ; tests dans un environnement isolé | ACCEPTÉ | RAPPORTÉ PAR L'UTILISATEUR |
| D-010 | 2026-11-04 | Ce dépôt est documentaire et séparé de la production ; fiabilité par statuts ; écritures de Claude via branche et pull request fusionnée par Émilien ; pas de ZIP | ACCEPTÉ | RAPPORTÉ PAR L'UTILISATEUR |
| D-011 | 2026-11-04 | Connecteur `carburant-mcp` : option « paramètre `repo` » retenue, avec liste blanche des deux dépôts | ACCEPTÉ | RAPPORTÉ PAR L'UTILISATEUR |
| D-012 | 2026-11-04 | Protocole de mémoire partagée ChatGPT/Claude : ordre de lecture de démarrage, statuts de transmission des paquets (EN ATTENTE DE TRANSMISSION, EN ATTENTE D'INTÉGRATION, INTÉGRÉ), paquet de transfert ChatGPT → Claude, journal quotidien avec sections `[Claude]` / `[ChatGPT]`, objectifs et principes dans `MANIFESTE.md`, registre des versions dans `codes/README.md` ; mise en œuvre par une seule PR `protocole-memoire`. Texte détaillé et règles de référence : [REGLES_DE_TRAVAIL.md](REGLES_DE_TRAVAIL.md). Règle de statut : un paquet ne reçoit le statut INTÉGRÉ qu'après vérification de la fusion effective dans `main` (relecture de `main`), jamais à sa réception ni à l'ouverture d'une PR | ACCEPTÉ | RAPPORTÉ PAR L'UTILISATEUR |
| D-013 | 2026-11-04 | Ne pas modifier le Worker `carburant-mcp` pour le moment ; le point d'accès restreint pour ChatGPT et les outils de lecture de l'historique restent des propositions futures (voir [AVANCEMENT.md](AVANCEMENT.md)) | ACCEPTÉ | RAPPORTÉ PAR L'UTILISATEUR |

## Conventions de travail acceptées

- Fichiers complets plutôt que modifications partielles, pour le code de l'app. RAPPORTÉ PAR L'UTILISATEUR.
- Le texte « À propos » de l'app ne change que sur demande (son contenu exact est dans l'app, il n'est pas dupliqué ici).
