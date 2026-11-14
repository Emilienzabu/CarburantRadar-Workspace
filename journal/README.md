# Journal

**Un fichier par jour** de travail, nommé `AAAA-MM-JJ.md`, avec **une section par assistant et par session**.

## Format d'un fichier journal

- Titre : `# Journal du AAAA-MM-JJ`.
- Une section `## [Claude] — titre de la session` ou `## [ChatGPT] — titre de la session`, au format en 11 sections de [../modeles/compte_rendu_session.md](../modeles/compte_rendu_session.md) (partie 1).
- Plusieurs sessions le même jour : plusieurs sections dans le même fichier, sans toucher à celles de l'autre assistant.
- **Paquet de transfert ChatGPT → Claude** : Claude le place dans une section `[ChatGPT]` en deux temps. D'abord un **compte rendu synthétique en 11 sections**, puis, sous le sous-titre `### Paquet de transfert reçu (intégral)`, le **paquet conservé intégralement**, tel que reçu (rien n'est résumé, supprimé ni reformulé : preuves, hypothèses, extraits de code, propositions non validées, prochaines actions), dans un bloc à quatre accents graves. L'en-tête du paquet reste tel que reçu ; le statut courant est suivi dans [../AVANCEMENT.md](../AVANCEMENT.md) et [../CHANGELOG.md](../CHANGELOG.md) ([../REGLES_DE_TRAVAIL.md](../REGLES_DE_TRAVAIL.md), sections 3 et 8).
- Un journal ne se réécrit pas : une correction passe par une nouvelle entrée.
- Le fichier du 2026-11-04 a été commencé avant ce format ; son contenu d'origine est conservé tel quel (c'est une session `[Claude]`) et la session suivante du jour y est ajoutée à la suite.

## Index (du plus récent au plus ancien)

La **première ligne** est le dernier journal à lire au début d'une conversation.

| Date | Résumé |
|---|---|
| [2026-11-12](2026-11-12.md) | [Claude] Archive `carburantradar_etape76.zip` (prototype Radar V51 à V76) : import fidèle dans `radar-v76/` (75 fichiers vérifiés par SHA-256), Worker candidat snapshot France V2 immuable, API garage par compte (authentification non implémentée : code de `carburant-proxy` inaccessible), documentation, rollback ; 541/541 tests du prototype + 61/61 tests V2 sur clone propre ; **PR #39 du dépôt de production (non fusionnée, rien déployé, seul `radar-v76/` touché)** ; risque : GitHub Pages rendrait le dossier public (branche `claude/radar-v76-2026-11-12`) |
| [2026-11-08](2026-11-08.md) | [Claude] 2 sessions. (1) Paquet V108 (prototype anti-doublon local) : comparé à `0001`, protocole `slot_id` + `sha256` testé sur modèle de référence, PR #35 (fusionnée). (2) `WORKER.pdf` : six constats sur `video-automation` vérifiés par exécution sur le code du PDF (tous confirmés, version déployée non vérifiée), extension `0002`, Worker candidat, générateur compatible, 130 tests Python + 36 tests JS, **PR #36 du dépôt de production (non fusionnée, rien déployé)** ; AVANCEMENT/CHANGELOG/DECISIONS non mis à jour (branche `claude/worker-ledger-2026-11-08`) |
| [2026-11-07](2026-11-07.md) | [Claude] Audit de l'archive V100 contre le code réel : tests V100 reproduits (295 + 3), encodage conforme Reels, contrôle avant publication, envois incertains/partiels, schéma D1 candidat (non validé sur D1), PR #34 du dépôt de production (non fusionnée) ; rapport [audits/AUDIT_V100_2026-11-07.md](../audits/AUDIT_V100_2026-11-07.md) (branche `claude/audit-v100-2026-11-07`) |
| [2026-11-06](2026-11-06.md) | [Claude] Paquet ChatGPT du 2026-11-06 : audit du code réel, garde astuce (PR #33 du dépôt de production, fusionnée : commit `d40c3c3`), audit E0/E1 archivé, décisions D-014 à D-016 (branche `claude-2026-11-06-securisation-videos`) |
| [2026-11-05](2026-11-05.md) | [ChatGPT] Paquet de transfert (plan de corrections et d'améliorations) reçu et intégré par Claude, avec vérification contre le code vidéo lu (branche `integration-paquet-chatgpt-2026-11-05`) |
| [2026-11-04](2026-11-04.md) | [Claude] Création du workspace, connecteur multi-dépôts ; [Claude] protocole de mémoire partagée (branche `protocole-memoire`) |

Après chaque session : ajouter ou compléter la ligne correspondante (en haut du tableau) et mettre à jour [../AVANCEMENT.md](../AVANCEMENT.md) si le travail le concerne.
