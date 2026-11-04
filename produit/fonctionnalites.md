# Fonctionnalités

Source : README de production lu le 2026-11-04 (VÉRIFIÉ pour ce que le README affirme ; le comportement réel de l'app n'a pas été testé par Claude).

## Radar

- Géolocalisation, choix du carburant (Diesel, SP95, SP98, E10, E85, GPL), rayon ajustable (5, 10, 20 ou 50 km selon le README ; 50 km : À CONFIRMER, voir [../AVANCEMENT.md](../AVANCEMENT.md)).
- Classement par score combiné prix et temps de trajet réel ; badge « Meilleur ratio » ; indicateur 24h/24 ; renommage et favoris.

## Véhicules et coût total

Plusieurs véhicules (nom, capacité du réservoir, consommation), véhicule par défaut ; classement par coût total : plein (environ 80 % du réservoir) plus trajet aller-retour. VÉRIFIÉ pour « appliqué » (SEO_REPORT, 3 pays) ; détails de la formule : RAPPORTÉ PAR L'UTILISATEUR (2026-10-24).

## Carte, Trajet, Analyse

- Carte Leaflet avec prix sur les marqueurs.
- Trajet : meilleure station sur le trajet vers une destination, arbitrage prix et détour, ouverture dans Google Maps.
- Analyse : historique 7 j / 1 mois / 3 mois / 1 an, zoom, comparaison à la moyenne de zone, plusieurs analyses en accordéon. Désactivée pour l'Espagne et l'Italie (RAPPORTÉ PAR L'UTILISATEUR).

## Alertes

Notifications Web Push quand une station passe sous un seuil par rapport à la moyenne locale ; logique anti-spam sur changement d'état ; clic ouvrant la station concernée (correctif rapporté).

## Compte et repères

Compte email + mot de passe, synchronisation entre appareils, usage possible sans compte ; repères personnels (domicile, travail) et destinations favorites.

## Autres

Thème sombre, icônes SVG, PWA installable, pages légales, page `/guide/`, tutoriel de démarrage et menu en 4 onglets (France ; portage ES/IT : À CONFIRMER).
