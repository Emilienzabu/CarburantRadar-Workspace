# Worker `carburant-proxy`

Code **hors dépôt** (dans Cloudflare). Tout ce qui suit est RAPPORTÉ PAR L'UTILISATEUR (sessions antérieures) et À CONFIRMER tant que le code n'est pas relu.

## Rôle

Proxy vers les API de prix, comptes utilisateurs et favoris, alertes push, suivi d'usage.

## Routes et fonctions connues

- Route `/es` : Espagne, source ministérielle espagnole, plusieurs provinces avec marge de sécurité, cache de 30 minutes via Cache API.
- Route `/it` : Italie, deux CSV nationaux quotidiens du ministère, stockés dans D1 (binding `DB_ITALIE`, table `stations_it`), rafraîchissement automatique si les données ont plus de 20 h.
- `/track` : suivi d'usage ; reçoit éventuellement `ville` envoyée par le client (préférée à la ville issue de l'IP).
- `/admin/users` et `/admin/day-users?jour=AAAA-MM-JJ` : comptes avec dernière ville connue ; détail des connexions d'un jour.
- Table `usage_days` : colonnes dont email et ville.
- Alertes : abonnements en KV `SUBS`, comptes en KV `USERS`, cron quotidien `10 5 * * *` (UTC), Web Push implémenté à la main (VAPID, RFC 8291/8292).

## Points à vérifier

- Protection d'accès des routes `/admin/*` : À CONFIRMER (voir [../audits/securite_confidentialite.md](../audits/securite_confidentialite.md)).
- Correction « nom renommé dans la notification » du 2026-10-14 : appliquée côté Worker ? À CONFIRMER.
- Cache de repli pour l'API espagnole (décision D-006 dans [../DECISIONS.md](../DECISIONS.md)) : état À CONFIRMER.
