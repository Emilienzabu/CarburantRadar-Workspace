AUDIT — WORKER CARBURANT PROXY

Projet : CarburantRadar
Composant : Worker Carburant Proxy
Fichier observé : "src/worker.js" (code compilé fourni dans la conversation)
Date de l'audit : 4 novembre 2026
Statut : Audit statique terminé — aucune modification effectuée

---

1. Rôle général

Le Worker Carburant Proxy est un composant central de CarburantRadar.

Il assure plusieurs fonctions :

- Recherche de stations et de prix en France.
- Recherche de stations et de prix en Espagne.
- Recherche de stations et de prix en Italie.
- Gestion des comptes utilisateurs.
- Synchronisation des favoris, noms personnalisés, repères et préférences.
- Gestion des abonnements aux notifications.
- Calcul des alertes de prix et envoi de notifications Web Push.
- Suivi statistique de l'utilisation.
- Administration et consultation des utilisateurs.

Il ne s'agit donc pas d'un simple proxy HTTP : il constitue une partie importante du backend de l'application.

2. Routes identifiées

Route| Fonction
"/"| Recherche de stations françaises
"/es"| Recherche de stations espagnoles
"/it"| Recherche de stations italiennes
"/register"| Inscription
"/login"| Connexion
"/logout"| Déconnexion
"/account" GET| Lecture du compte
"/account" POST| Mise à jour des données du compte
"/subscribe"| Création d'un abonnement Push
"/unsubscribe"| Suppression d'un abonnement
"/update-names"| Modification des noms personnalisés
"/track"| Suivi statistique
"/admin/stats"| Statistiques générales
"/admin/day-users"| Utilisateurs d'une journée
"/admin/users"| Liste des comptes

Le Worker possède également un traitement planifié "scheduled()" pour le contrôle des prix et l'envoi des notifications.

3. Sources de données

France

- Source : dataset officiel des prix des carburants.
- API : Explore v2.1.
- Filtrage géographique : "within_distance()" sur le champ "geom".
- Cache en mémoire : 10 minutes.

Espagne

- Source : Ministerio para la Transición Ecológica.
- API : service REST officiel des stations par province.
- Sélection des provinces à partir de coordonnées de référence.
- Vérification finale avec la formule de Haversine.
- Cache des provinces : 30 minutes.
- Traitement tolérant aux pannes partielles.

Italie

- Source : MIMIT.
- Fichiers : "anagrafica_impianti_attivi.csv" et "prezzo_alle_8.csv".
- Import dans Cloudflare D1.
- Actualisation déclenchée lorsque la base dépasse 20 heures.
- Recherche géographique par rectangle puis vérification Haversine.

4. Stockage et services Cloudflare

Variables et ressources identifiées dans le code :

- "USERS" : comptes et sessions.
- "SUBS" : abonnements aux notifications.
- "DB_STATS" : statistiques d'utilisation.
- "DB_ITALIE" : base des stations italiennes.
- "VAPID_PRIVATE_KEY" : clé privée VAPID, à conserver exclusivement comme secret.
- "ADMIN_SECRET" : clé de protection de l'administration.
- "VAPID_PUBLIC" et coordonnées publiques : paramètres publics du service Push.

Les noms des ressources sont ceux présents dans le code fourni. Leur configuration réelle dans Cloudflare n'a pas été vérifiée pendant cet audit.

5. Points techniques positifs

- Utilisation de sources officielles de données.
- Vérification géographique réelle en Espagne et en Italie.
- Stockage local des données italiennes pour éviter de télécharger les CSV à chaque recherche.
- Utilisation de D1 et KV pour des responsabilités distinctes.
- Hachage des mots de passe avec PBKDF2-SHA256.
- Sessions aléatoires avec expiration.
- Comparaison des clés d'administration sans arrêt anticipé sur les caractères.
- Chiffrement des notifications Web Push avec ECDH et AES-GCM.
- Nettoyage des abonnements expirés lorsque le serveur Push répond 404 ou 410.
- Gestion des pannes partielles dans la récupération des données espagnoles.

6. Anomalies et risques identifiés

P0 — À traiter en priorité

Import italien non atomique

Un échec après plusieurs lots peut laisser une base partiellement actualisée. La date "maj" maximale peut alors donner une fausse impression de fraîcheur.

Fiabilité des alertes

La moyenne locale est calculée sur un maximum de 100 stations sans pagination ni tri explicite. Les prix ne sont pas filtrés selon leur ancienneté avant le calcul.

Sécurité des abonnements Push

Les endpoints sont insuffisamment restreints. Les clés d'abonnement permettent de modifier ou supprimer un abonnement et les données "names" ne sont pas suffisamment validées.

P1 — À traiter ensuite

Cache français

Les coordonnées sont arrondies à 0,01 degré pour construire la clé de cache, alors que la requête utilise les coordonnées exactes. Des recherches proches peuvent donc partager des résultats géographiques différents.

Réponses de l'API française

Le statut HTTP de la réponse distante n'est pas vérifié avant la mise en cache.

Couverture espagnole

La sélection des provinces repose sur leurs centres, une marge fixe de 90 km et un maximum de six provinces. Certaines stations proches peuvent être omises.

Comptes

Absence de limitation des tentatives de connexion et d'inscription, risque de concurrence lors de l'inscription et absence de limites détaillées sur les données synchronisées.

Statistiques et confidentialité

Le suivi peut enregistrer un identifiant, un email et une ville. Les durées de conservation et les modalités de suppression doivent être documentées. Les périodes "last7" et "last30" comprennent respectivement huit et 31 jours.

P2 — Améliorations structurelles

- Ajouter une journalisation exploitable.
- Ajouter des indicateurs de réussite et d'échec des imports.
- Ajouter des délais maximums et des reprises sur les appels externes.
- Encadrer les paramètres "dist" et "limit".
- Envisager une séparation logique des modules.
- Ajouter des tests automatisés pour les cas géographiques et les imports.

7. Recommandations de conception

1. Rendre l'import italien atomique ou utiliser une stratégie de versionnement permettant de conserver l'ancienne base jusqu'à validation complète du nouvel import.
2. Vérifier la date réelle des données, pas seulement la date du téléchargement.
3. Paginer ou sélectionner de manière déterministe les stations utilisées pour les moyennes.
4. Vérifier la fraîcheur de chaque prix avant de déclencher une alerte.
5. Renforcer la validation des endpoints et des données d'abonnement.
6. Améliorer la précision du cache français.
7. Sélectionner les provinces espagnoles à partir de leur couverture géographique réelle.
8. Ajouter une journalisation et un suivi des erreurs.
9. Définir les durées de conservation des données personnelles et les moyens de suppression.

8. Limites de cet audit

Cet audit repose sur le code fourni dans la conversation.

Les éléments suivants n'ont pas été vérifiés :

- Configuration réelle des bindings Cloudflare.
- Valeurs des secrets Cloudflare.
- Correspondance effective des clés VAPID.
- Fréquence réelle du déclencheur "scheduled()".
- Résultats de tests en production.
- Contenu exact des fichiers CSV téléchargés pendant l'exécution.
- Comportement réel des applications clientes face aux réponses du Worker.

Le code reçu semble être une version compilée de "src/worker.js". Il ne remplace pas l'archivage du code source original, de sa configuration et de ses éventuels fichiers de tests.

9. Historique des modifications

Aucune modification réalisée pendant cet audit.

Aucun déploiement Cloudflare, aucune modification de base D1 ou KV, aucun changement de secret et aucun changement du code de production.

10. Consigne pour les prochains audits

Avant toute modification :

1. Relire le présent audit.
2. Retrouver le code source original et son historique Git.
3. Vérifier les configurations Cloudflare nécessaires.
4. Reproduire les anomalies avec des tests.
5. Établir un plan de correction.
6. Faire valider les modifications avant tout déploiement.

Statut final : composant fonctionnellement riche, avec une bonne base technique, mais plusieurs risques de fiabilité et de sécurité à traiter avant de considérer le backend comme pleinement robuste.
