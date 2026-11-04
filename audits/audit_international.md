# Audit international

Base : `SEO_REPORT.md` (données du 03/11/2026) et notes rapportées.

## Espagne

- Source : API officielle du ministère ; 11 441 stations exploitables au dernier rapport ; 455 pages villes (454 indexables, 352 ajoutées automatiquement), 50 pages provinces. VÉRIFIÉ.
- App : traduite en espagnol ; mode Analyse et statut ouvert/fermé désactivés faute de données compatibles. RAPPORTÉ PAR L'UTILISATEUR.
- Cache de repli quand l'API coupe la connexion : traité en priorité (D-006), état réel À CONFIRMER.

## Italie

- Source : deux CSV nationaux quotidiens du ministère, stockés dans D1 ; app traduite en italien ; Analyse et statut ouvert/fermé désactivés. RAPPORTÉ PAR L'UTILISATEUR.
- **Au dernier rapport SEO : source indisponible**, téléchargement de `prezzo_alle_8.csv` en dépassement de délai ; cache de secours en HTTP 404 ; pages historiques conservées. VÉRIFIÉ (SEO_REPORT).
- Cause du dépassement de délai : HYPOTHÈSE (lenteur ou blocage côté ministère, côté exécuteur GitHub). Correction : PROPOSITION (nouvelle tentative, cache déposé, répétition à une autre heure).
- Les 558 villes et 52 hubs ES/IT du rapport sont comptés ensemble : ventilation par pays À CONFIRMER hors Espagne.

## Autres pays

- Open data confirmée exploitable : Portugal, Allemagne (Tankerkönig), Royaume-Uni, Autriche, Grèce ; non implémentés. RAPPORTÉ PAR L'UTILISATEUR.
- Écartés : Belgique et Luxembourg (pas de données par station), Algérie et Tunisie (prix fixés nationalement, rien à comparer), Maroc (pas d'open data). RAPPORTÉ PAR L'UTILISATEUR.

Quel pays ajouter ensuite n'est pas décidé : voir [../produit/idees_et_ameliorations.md](../produit/idees_et_ameliorations.md).
