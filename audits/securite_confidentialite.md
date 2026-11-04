# Audit sécurité et confidentialité

Base : README de production, code du Worker `carburant-mcp`, notes rapportées. **Le code du Worker `carburant-proxy` n'a pas été audité.**

## Connecteur `carburant-mcp` (VÉRIFIÉ par lecture du code)

- Secret dans l'URL, 404 sans lui ; comparaison à temps constant.
- Aucune écriture sur `main`/`master` ; `.github/` et chemins `..` refusés ; liste blanche de deux dépôts (v1.1.0).
- Risque résiduel : si le jeton GitHub a plus de droits que nécessaire, le garde-fou repose sur le Worker seul. Périmètre réel du jeton : À CONFIRMER.

## App et comptes (déclaré dans le README : À CONFIRMER dans le code)

- Hachage PBKDF2 100 000 itérations, XSS échappé, validation des endpoints, limite d'inscriptions.
- Pas de récupération de mot de passe (décision D-007).

## Données personnelles collectées (RAPPORTÉ PAR L'UTILISATEUR)

- Comptes email + mot de passe haché ; favoris et préférences synchronisés.
- `usage_days` : email et ville par jour de connexion ; ville issue de l'IP ou, si l'utilisateur a accordé la géolocalisation, d'un géocodage inverse via Nominatim (coordonnées envoyées à un service tiers).
- Google Analytics ; AdSense (balise sur le site racine, pas de publicités actives).

## Points à traiter (PROPOSITION)

- Vérifier que les routes `/admin/*` exigent une authentification forte.
- Vérifier que la politique de confidentialité mentionne : stockage de la ville par compte, géocodage inverse tiers, Google Analytics.
- Bannière de consentement avant toute activation de publicités (décision D-007 : pas avant les pubs).
- Ancien serveur MCP sur Render : l'URL affichait « Unauthorized » et un avertissement navigateur (2026-09-28, RAPPORTÉ PAR L'UTILISATEUR). S'il n'est plus utilisé, le désactiver ; décision à prendre par Émilien.
- Ajouter les noms de secrets réellement utilisés par les workflows dans [../SECURITE_ET_SECRETS.md](../SECURITE_ET_SECRETS.md).
