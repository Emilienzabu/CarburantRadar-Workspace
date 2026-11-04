# Audit de l'application et des pages SEO

Base : lecture du README et du `SEO_REPORT.md` du dépôt de production (2026-11-04). Aucun test de l'app n'a été exécuté par Claude pendant cette mission.

## Constats VÉRIFIÉS (SEO_REPORT, données du 03/11/2026)

- 418 pages France générées : 182 villes (178 indexables, 4 en noindex), 79 départements, 13 régions, 143 pages ville + carburant, 1 hub. 885 URLs au sitemap.
- Unicité des balises : titres, meta descriptions, H1 et canonicals tous distincts (418/418).
- Aucune page sous 250 mots, aucune page orpheline indexable ; liens internes : moyenne 10,1 par page.
- Contenu unique moyen : 50 % (pages villes), 32 % (ville + carburant), 44 % (départements/régions) ; aucune paire quasi identique.
- Validation : 0 erreur, 3 avertissements : `/france/`, `/espagne/`, `/italie/` contiennent 5 balises H1 chacune.
- 18 pages villes sans ville voisine affichée ; 4 pages en noindex pour manque de données.

## Problèmes et pistes

| Point | Statut |
|---|---|
| 5 balises H1 sur les pages d'app de chaque pays | VÉRIFIÉ (avertissement) ; impact SEO : HYPOTHÈSE ; correction : PROPOSITION |
| Option de rayon 50 km : listée par le README, abandonnée selon une note ancienne | À CONFIRMER |
| Portage ES/IT de fonctions déjà faites sur France (menu 4 onglets, tutoriel, bouton installer, etc.) | À CONFIRMER |
| Sitemap illisible dans Search Console malgré un test en direct réussi | RAPPORTÉ PAR L'UTILISATEUR ; cause : non établie |
| Gazole : 61 pages, SP95 : 2, GPL : 0 sur les pages ville + carburant | VÉRIFIÉ ; interprétation (couverture inégale des carburants) : HYPOTHÈSE |

## À faire pour un audit complet (PROPOSITION)

- Test réel sur mobile : géolocalisation, notifications, installation PWA.
- Lecture du code `france/index.html` pour confirmer les correctifs listés dans [../AVANCEMENT.md](../AVANCEMENT.md).
