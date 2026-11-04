# Données et sources

## France

- Prix en temps réel : jeu officiel « Prix des carburants en France, flux instantané v2 » sur data.economie.gouv.fr. VÉRIFIÉ (nom cité dans SEO_REPORT, dernière mise à jour de prix enregistrée : 03/11/2026 13:30 UTC ; 9 823 stations analysées).
- Historique : jeu `prix-des-carburants-j-1` sur public.opendatasoft.com. RAPPORTÉ PAR L'UTILISATEUR.
- Historique conservé pour les pages SEO : 30 jours (2026-10-02 au 2026-11-03). VÉRIFIÉ (SEO_REPORT).
- Parité vérifiée sur une station : gazole 2,179 € identique sur XML, API et site officiel (03/11/2026 11:58:50). RAPPORTÉ PAR L'UTILISATEUR (cellule C).

## Leçons d'API (RAPPORTÉ PAR L'UTILISATEUR, anciennes ; À CONFIRMER)

- Ne jamais deviner les noms de champs ou la syntaxe géographique.
- Le champ `geo_point` du jeu historique est vide : récupérer d'abord les identifiants de stations via le proxy temps réel, puis interroger l'historique par identifiants.
- Plafond de 100 résultats par requête.
- Syntaxe géographique : une note indique `geofilter.distance` (virgules encodées), une autre `within_distance(geom, geom'POINT(lon lat)', Xm)` sur le champ `geom` pour l'API v2.1. Laquelle est utilisée aujourd'hui : À CONFIRMER dans le code.

## Espagne et Italie

Voir [../audits/audit_international.md](../audits/audit_international.md). Espagne : API officielle du ministère, cache de 30 minutes. Italie : CSV nationaux quotidiens du ministère stockés en D1.

## Autres services

Nominatim (géocodage), OSRM (itinéraires), OpenStreetMap (tuiles). VÉRIFIÉ (README).

## Limites déclarées

Les prix peuvent changer entre deux mises à jour officielles et dépendent des déclarations des stations. VÉRIFIÉ (README).
