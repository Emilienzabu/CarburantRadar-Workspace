# Audits

Audits techniques. Un audit distingue toujours ce qui est VÉRIFIÉ (code lu, test exécuté) de ce qui est HYPOTHÈSE ou PROPOSITION.

| Fichier | Sujet |
|---|---|
| [audit_application.md](audit_application.md) | App et pages SEO |
| [audit_videos.md](audit_videos.md) | Générateur et publication vidéo |
| [AUDIT_E0_E1_2026-11-05.md](AUDIT_E0_E1_2026-11-05.md) | Résultats réels du diagnostic E0/E1 : filtre géographique des vidéos, exhaustivité de la référence, erreur gzip, fraîcheur des prix |
| [AUDIT_V100_2026-11-07.md](AUDIT_V100_2026-11-07.md) | Audit de l'archive V100 contre le code réel : tests reproduits, encodage Reels, contrôle avant publication, anti-doublon, schéma D1 candidat, origine du 480 × 854 (hypothèses), comparaison V100 / code intégré |
| [AUDIT_WORKER_CARBURANT_PROXY_2026-11-04.md](AUDIT_WORKER_CARBURANT_PROXY_2026-11-04.md) | Worker `carburant-proxy` (snapshot compilé, à relire contre le code déployé) |
| [securite_confidentialite.md](securite_confidentialite.md) | Sécurité, confidentialité, comptes |
| [audit_international.md](audit_international.md) | Espagne et Italie, autres pays |

## Quatre catégories à ne jamais mélanger

| Catégorie | Définition | Statut attendu |
|---|---|---|
| Problème constaté | Observé réellement, preuve citée (code lu, test exécuté, sortie réelle) | VÉRIFIÉ |
| Risque potentiel | Conséquence plausible non constatée à ce jour | À CONFIRMER ou HYPOTHÈSE |
| Hypothèse | Explication possible, non démontrée | HYPOTHÈSE |
| Proposition | Correction ou amélioration suggérée, non décidée | PROPOSITION |

Une hypothèse ne devient VÉRIFIÉE qu'avec une preuve. Une proposition ne devient décision qu'avec l'accord explicite d'Émilien.

## Documenter une découverte

Chaque découverte importante indique : sujet ; statut ; date ; fichiers concernés ; preuves ou éléments de vérification ; conséquences ; prochaine action.

Modèle de fiche pour un problème : [../modeles/fiche_anomalie.md](../modeles/fiche_anomalie.md).
