# Mesure de la performance

## Besoin exprimé (RAPPORTÉ PAR L'UTILISATEUR, 2026-11-04)

- Analyse des performances par les **API officielles** des plateformes.
- Comparaison à 24 h, 48 h et 7 jours après publication.
- UTM et Google Analytics 4 pour relier vidéos et visites.
- Solution gratuite ou presque.

## Existant

| Élément | Détail | Statut |
|---|---|---|
| Liens publiés par le générateur | `https://carburantradar.fr` sans UTM, racine uniquement ; Instagram : « lien en bio » | VÉRIFIÉ (`video/donnees.py`) |
| Google Analytics (gtag) | Cité dans le README ; version GA4 non vérifiée | VÉRIFIÉ pour la mention ; version : À CONFIRMER |
| `track.js` | Fichier de 701 octets à la racine ; contenu non lu | À CONFIRMER |
| Route `/track` du Worker | Usage quotidien (`usage_days`), ville, email | RAPPORTÉ PAR L'UTILISATEUR |
| Page `admin/` | Graphique d'usage par jour, détail des connexions, comptes avec ville | RAPPORTÉ PAR L'UTILISATEUR |

Conséquence : aujourd'hui, rien dans l'URL ne dit quelle vidéo, quel format ou quelle ville a amené une visite. Effet réel sur les rapports GA : HYPOTHÈSE (le site référent peut apparaître, sans le détail par vidéo).

## Indicateurs proposés (PROPOSITION)

- Par publication : vues, durée de visionnage, clics ou visites, nouveaux utilisateurs attribués (UTM).
- Par format et par ville : visites par publication, pour décider quoi produire.
- Fenêtres de lecture : 24 h, 48 h, 7 j.
- Seuil de succès : à définir avec Émilien (non décidé).

## À vérifier avant de bâtir la mesure

- Quelles données les API officielles YouTube et Instagram exposent, avec quels quotas et quelles autorisations : À CONFIRMER.
- Où stocker les résultats par publication (le numéro de publication `k` existe déjà dans le générateur) : à décider.
- Pistes côté liens : [../audits/audit_videos.md](../audits/audit_videos.md), problème n° 3.
