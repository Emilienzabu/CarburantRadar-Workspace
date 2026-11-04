# Stratégie éditoriale

## Vidéos (VÉRIFIÉ dans `video/generate_video.py`)

- Deux créneaux quotidiens (matin, soir) ; trois formats qui alternent : `ville` (top 3 d'une ville et économie sur un plein), `classement` (villes les moins chères), `astuce` (conseil sans chiffres).
- Principe de fond : des prix réels, pas de chiffres inventés (le format `astuce` évite les chiffres).
- Détails techniques : [../codes/worker_video.md](../codes/worker_video.md).

## Pages SEO (VÉRIFIÉ, SEO_REPORT)

- Contenu basé sur des données réelles, pas de pages à contenu mince : 4 pages villes en noindex faute de données suffisantes.
- Contraintes décidées : ne rien inventer, ne casser aucune URL existante (RAPPORTÉ PAR L'UTILISATEUR).

## Ligne éditoriale (PROPOSITION)

- Ton factuel et utile : l'économie concrète pour le lecteur, la source officielle citée.
- Une idée par vidéo ; une ville ou un carburant précis plutôt que des généralités.
- Cohérence avec la règle de confiance : aucun classement influencé par une station ([../DECISIONS.md](../DECISIONS.md), D-004).

Améliorations visuelles et qualitatives : [../audits/audit_videos.md](../audits/audit_videos.md).
