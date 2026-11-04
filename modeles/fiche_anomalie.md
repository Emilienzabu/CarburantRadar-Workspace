# Modèle : fiche anomalie

À copier dans le fichier d'audit concerné (voir [../audits/README.md](../audits/README.md)). Distinguer : problème constaté (VÉRIFIÉ), risque potentiel, hypothèse, proposition.

```
## Titre de l'anomalie

- Date de constat :
- Où : fichier, page, route, Worker
- Fichiers concernés (dépôt, chemin, branche, version ou date de lecture) :
- Symptôme (VÉRIFIÉ si reproduit, sinon RAPPORTÉ PAR L'UTILISATEUR) :
- Étapes pour reproduire :
- Preuves ou éléments de vérification :
- Cause : HYPOTHÈSE ou VÉRIFIÉ (avec preuve)
- Correction proposée : PROPOSITION
- Impact et conséquences :
- Prochaine action :
- Statut : EN COURS / TERMINÉ / BLOQUÉ
```

Après correction réelle : noter la date et la preuve du test dans le champ Statut (comportement avant/après, tests réalisés et résultats), puis mettre à jour [../AVANCEMENT.md](../AVANCEMENT.md).
