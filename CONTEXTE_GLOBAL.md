# Contexte global

Mis à jour : 2026-11-04. Statuts définis dans [REGLES_DE_TRAVAIL.md](REGLES_DE_TRAVAIL.md).

## Qu'est-ce que CarburantRadar

- Application web progressive (PWA) gratuite pour trouver les stations-service les moins chères autour de soi, suivre l'évolution des prix et recevoir des alertes. **VÉRIFIÉ** (README du dépôt de production, lu le 2026-11-04).
- Principe : s'appuyer sur les données publiques officielles pour comparer les prix sans ouvrir plusieurs sites. **VÉRIFIÉ** (README).
- Pays : France, Espagne, Italie (un dossier `france/`, `espagne/`, `italie/` à la racine du dépôt de production). **VÉRIFIÉ** (listing du dépôt + rapport SEO).
- Auteur et propriétaire : Émilien. Le projet est présenté sous le nom « Zabukovec Company ». **RAPPORTÉ PAR L'UTILISATEUR** (ancien).

## Dépôts et services

| Élément | Rôle | Statut |
|---|---|---|
| `Emilienzabu/CarburantRadar` | Production : app, pages SEO générées, générateur, `video/`, admin | VÉRIFIÉ (lecture) |
| `Emilienzabu/CarburantRadar-Workspace` | Ce dépôt documentaire privé | VÉRIFIÉ |
| `Emilienzabu/emilienzabu.github.io` | Site racine du domaine (balise AdSense, robots.txt) | RAPPORTÉ PAR L'UTILISATEUR (2026-10-08) |
| `Emilienzabu/github-mcp-server` (Render) | Ancien serveur MCP GitHub | À CONFIRMER (peut ne plus servir, remplacé par `carburant-mcp`) |
| Worker `carburant-proxy` (Cloudflare) | Proxy API, comptes, alertes, tracking, Espagne/Italie | RAPPORTÉ PAR L'UTILISATEUR (code hors dépôt) |
| Worker `video-automation` (Cloudflare) | Réception des vidéos et publication YouTube/Instagram | VÉRIFIÉ pour l'URL et le contrat d'appel (code de `video/generate_video.py`) ; code du Worker non lu : À CONFIRMER |
| Worker `carburant-mcp` (Cloudflare) | Connecteur MCP de Claude vers les dépôts GitHub | VÉRIFIÉ (code relu et modifié en session) |

Détails : [INVENTAIRE_TECHNIQUE.md](INVENTAIRE_TECHNIQUE.md).

## Domaine

Un fichier `CNAME` (17 octets) existe à la racine du dépôt de production et le rapport SEO cite `carburantradar.fr`. Contenu exact du CNAME non lu : **À CONFIRMER** que `carburantradar.fr` est le domaine actif.

## Audience actuelle

Environ 3-4 utilisateurs par jour. **RAPPORTÉ PAR L'UTILISATEUR** (2026-10-17) ; à rafraîchir via le tableau d'administration.

## Façon de travailler (historique)

- Déploiements historiquement par copier-coller (GitHub web mobile, éditeur Cloudflare), sans CLI ni build. **RAPPORTÉ PAR L'UTILISATEUR** (ancien ; À CONFIRMER aujourd'hui, un connecteur d'écriture existe désormais).
- Préférence : fichiers complets plutôt que diffs partiels. **RAPPORTÉ PAR L'UTILISATEUR**.

## Priorités

1. Croissance des utilisateurs avant monétisation (**ACCEPTÉ**, voir [DECISIONS.md](DECISIONS.md)).
2. Les vidéos courtes (YouTube Shorts, Instagram Reels) comme canal d'acquisition (**EN COURS**, voir [strategie/acquisition_utilisateurs.md](strategie/acquisition_utilisateurs.md)).
3. SEO : pages villes, départements, régions (voir [audits/audit_international.md](audits/audit_international.md) et [AVANCEMENT.md](AVANCEMENT.md)).
