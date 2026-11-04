# Données et sources

## France

- Prix en temps réel : jeu officiel « Prix des carburants en France, flux instantané v2 » sur data.economie.gouv.fr. VÉRIFIÉ (nom cité dans SEO_REPORT ; identifiant `prix-des-carburants-en-france-flux-instantane-v2` lu dans `video/donnees.py`). Dernière mise à jour de prix enregistrée : 03/11/2026 13:30 UTC ; 9 823 stations analysées (SEO_REPORT).
- Module vidéo : API `explore/v2.1`, filtre `geofilter.distance` au format `lat,lon,rayon_en_mètres`, champs `<carburant>_prix` et `<carburant>_maj`, pages de 100 résultats. VÉRIFIÉ (code de `video/donnees.py`, non exécuté).
- Historique : jeu `prix-des-carburants-j-1` sur public.opendatasoft.com. RAPPORTÉ PAR L'UTILISATEUR.
- Historique conservé pour les pages SEO : 30 jours (2026-10-02 au 2026-11-03). VÉRIFIÉ (SEO_REPORT).
- Parité vérifiée sur une station : gazole 2,179 € identique sur XML, API et site officiel (03/11/2026 11:58:50). RAPPORTÉ PAR L'UTILISATEUR (cellule C).

## Leçons d'API (RAPPORTÉ PAR L'UTILISATEUR, anciennes)

- Ne jamais deviner les noms de champs ou la syntaxe géographique.
- Le champ `geo_point` du jeu historique est vide : récupérer d'abord les identifiants de stations via le proxy temps réel, puis interroger l'historique par identifiants.
- Plafond de 100 résultats par requête.
- Syntaxe géographique : `geofilter.distance` est celle du module vidéo (VÉRIFIÉ dans le code). Une autre note ancienne cite `within_distance(geom, geom'POINT(lon lat)', Xm)` pour l'app ; syntaxe utilisée aujourd'hui par l'app et le Worker : À CONFIRMER dans leur code.

## Règles de qualité côté vidéo (VÉRIFIÉ code)

Prix retenus entre 0,8 et 3,5 € ; âge maximum 5 jours ; une seule entrée par adresse ; au moins 8 stations pour comparer une ville. Plein de référence fixe : 50 litres.

## Espagne et Italie

Voir [../audits/audit_international.md](../audits/audit_international.md). Espagne : API officielle du ministère, cache de 30 minutes. Italie : CSV nationaux quotidiens du ministère stockés en D1.

## Autres services

Nominatim (géocodage), OSRM (itinéraires), OpenStreetMap (tuiles). VÉRIFIÉ (README).

## Limites déclarées

Les prix peuvent changer entre deux mises à jour officielles et dépendent des déclarations des stations. VÉRIFIÉ (README).
