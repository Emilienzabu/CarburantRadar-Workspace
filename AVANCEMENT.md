# Avancement

État au 2026-11-04. Ce fichier est mis à jour à la fin de chaque session. Statuts : voir [REGLES_DE_TRAVAIL.md](REGLES_DE_TRAVAIL.md).

## EN COURS

| Chantier | Détail | Statut / source |
|---|---|---|
| Mission vidéo acquisition | Faire du générateur (`video/` + Worker `video-automation`) un canal d'acquisition ; règle : audit, puis plan validé, avant toute modification. Audit statique des modules Python fait (voir TERMINÉ) ; **aucun plan rédigé ni validé** ; Worker, workflows et résultats de génération non audités | EN COURS, RAPPORTÉ PAR L'UTILISATEUR |
| Diagnostics de données | Cellules A (fuseau XML/API), B (vidéo `--demo` + TTS), C (parité XML/API) | EN COURS ; seul résultat connu : station 56100009, gazole 2,179 € identique sur XML, API et site officiel (03/11/2026 11:58:50), RAPPORTÉ PAR L'UTILISATEUR |

## TERMINÉ

| Élément | Source |
|---|---|
| Architecture multi-pays (un dossier + `index.html` par pays, sélecteur de pays à la racine) | RAPPORTÉ PAR L'UTILISATEUR ; dossiers présents : VÉRIFIÉ |
| Espagne (route `/es`) et Italie (route `/it`, stockage D1) | RAPPORTÉ PAR L'UTILISATEUR ; pages ES/IT présentes dans le rapport SEO : VÉRIFIÉ |
| Correctifs notification (clic ouvre la station), scope du service worker, accordéon du menu, hreflang, page `/guide/` | RAPPORTÉ PAR L'UTILISATEUR |
| Refonte SEO du générateur de pages villes, fusionnée le 2026-09-30 | RAPPORTÉ PAR L'UTILISATEUR ; `SEO_REPORT.md` présent : VÉRIFIÉ |
| Véhicules multiples et classement par coût total (France, Espagne, Italie) | VÉRIFIÉ (SEO_REPORT : « appliqué » pour les 3 pays) |
| Correction du mot « l'instant » qui cassait 3 pages villes françaises | RAPPORTÉ PAR L'UTILISATEUR |
| Connecteur `carburant-mcp` v1.1.0 avec paramètre `repo` (liste blanche de 2 dépôts) | VÉRIFIÉ (branche créée et fichiers écrits sur le Workspace le 2026-11-04) |
| Workspace documentaire : 32 fichiers, PR #1 fusionnée par Émilien | VÉRIFIÉ (racine de `main` relue) |
| Audit statique de `video/` (`generate_video.py`, `donnees.py`, `audio.py`, `rendu.py`, `requirements.txt`, début de `musique.py`) : 8 problèmes listés dans [audits/audit_videos.md](audits/audit_videos.md) | TERMINÉ pour la lecture ; rien exécuté ni corrigé |

## À CONFIRMER (état incertain)

- Portage sur `espagne/` et `italie/` : menu en 4 onglets, bouton « Installer l'application », tutoriel de démarrage, bouton Snapchat, messages de géolocalisation distincts, ville précise (géocodage inverse). Notés « en attente » dans des sessions antérieures ; peuvent avoir été faits depuis. À vérifier dans le code.
- Option de rayon 50 km : le README de production la liste encore ; une note ancienne dit qu'elle a été abandonnée. À vérifier.
- Alertes : demande « priorité super importante » du 2026-10-14 (nom renommé dans la notification, clic vers la station) ; une correction du service worker est rapportée, la partie Worker n'est pas confirmée.
- Non lus : fin de `musique.py`, Worker `video-automation`, Worker `carburant-proxy`, contenu de `.github/` (bloqué par le connecteur).

## BLOQUÉ / problèmes ouverts

| Problème | Statut |
|---|---|
| Google Search Console : « Impossible de lire le sitemap » (`sitemap_1.xml` et `sitemap_2.xml`, contenu identique) | RAPPORTÉ PAR L'UTILISATEUR (2026-10-08) ; état actuel À CONFIRMER |
| Italie : source officielle indisponible au dernier rapport SEO (délai dépassé sur le CSV du ministère), cache de secours en HTTP 404 ; pages historiques conservées | VÉRIFIÉ (SEO_REPORT, données du 03/11/2026) |

Voir aussi [audits/](audits/README.md) et [produit/idees_et_ameliorations.md](produit/idees_et_ameliorations.md).
