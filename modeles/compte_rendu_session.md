# Modèles : compte rendu de session et paquet de transfert

Deux modèles dans ce fichier : (1) le compte rendu de session, (2) le paquet de transfert ChatGPT → Claude.

## 1. Compte rendu de session (Claude ou ChatGPT)

À copier dans `journal/AAAA-MM-JJ.md` (un fichier par jour ; si le fichier n'existe pas, commencer par `# Journal du AAAA-MM-JJ`). Une section par assistant et par session. Pour un paquet de transfert intégré, ce compte rendu synthétique vient **avant** le paquet conservé intégralement (partie 2).

~~~
## [Claude] — titre court de la session      (ou [ChatGPT])

### 1. Objectif

### 2. Travail effectué (avec statut : VÉRIFIÉ, TERMINÉ, EN COURS...)

### 3. Résultats et preuves

### 4. Problèmes identifiés

### 5. Décisions validées (renvoi vers DECISIONS.md, ou « aucune »)

### 6. Propositions en attente

### 7. Fichiers concernés et versions (dépôt, chemin, branche, commit ou date de lecture)

### 8. Tests effectués (et résultats réels, sinon « non testé »)

### 9. État final

### 10. Prochaine étape (action exacte)

### 11. Informations indispensables pour la prochaine session
~~~

Rappels : ne pas écrire de secret ni de donnée personnelle ; ne pas déclarer VÉRIFIÉ ce qui n'a pas été testé ; mettre à jour [../AVANCEMENT.md](../AVANCEMENT.md) et [../CHANGELOG.md](../CHANGELOG.md) seulement si le travail les concerne ; ajouter la ligne dans [../journal/README.md](../journal/README.md).

## 2. Paquet de transfert ChatGPT → Claude

Objectif : permettre à Claude de reprendre le travail de ChatGPT et de l'intégrer au Workspace sans qu'Émilien ait à réexpliquer. Règles complètes : [../REGLES_DE_TRAVAIL.md](../REGLES_DE_TRAVAIL.md), sections 3 et 8.

### Consigne à coller dans ChatGPT

~~~
Prépare un paquet de transfert pour Claude en suivant exactement le format ci-dessous, dans UN SEUL bloc de code délimité par quatre accents graves (````), que je pourrai copier d'un coup. À l'intérieur de ce bloc, mets chaque extrait de code dans un bloc à trois accents graves (```). N'écris rien en dehors du bloc. Remplis chaque rubrique (écris « aucun » ou « non testé » si besoin). Étiquette chaque information avec un statut : VÉRIFIÉ (avec la preuve), RAPPORTÉ PAR L'UTILISATEUR, À CONFIRMER, HYPOTHÈSE ou PROPOSITION. Sépare strictement les faits vérifiés, les hypothèses et les propositions. Ne mets dans « Décisions validées » que ce que j'ai explicitement accepté. N'écris aucun mot de passe, token, clé, secret, URL de connecteur ni donnée personnelle. Donne des extraits de code courts et indispensables, avec leur provenance (dépôt, chemin, branche, date de lecture).
~~~

### Format du paquet

Le paquet est délimité par **quatre** accents graves ; les extraits de code qu'il contient le sont par **trois** : le bloc extérieur ne se referme donc pas au premier extrait et reste copiable d'un coup. (Le cadre en tildes ci-dessous sert seulement à afficher le modèle.)

~~~~~~
````text
=== PAQUET DE TRANSFERT CHATGPT → CLAUDE ===
Statut de transmission : EN ATTENTE DE TRANSMISSION
Date : AAAA-MM-JJ
Auteur : ChatGPT (modèle ou version si connue)
Titre court :

## 1. Objectif de la session

## 2. Travail réalisé

## 3. Résultats vérifiés et preuves
(une ligne par résultat : fait — VÉRIFIÉ — preuve)

## 4. Hypothèses
(HYPOTHÈSE, jamais présentées comme des faits)

## 5. Propositions
(PROPOSITION, jamais présentées comme des décisions)

## 6. Fichiers et versions concernés
(dépôt, chemin, branche, commit ou date de lecture ; version réelle ou copie ancienne ?)

## 7. Codes ou extraits indispensables
(courts, avec provenance ; aucun secret. Chaque extrait dans un bloc à trois accents graves, comme ci-dessous.)

```python
# provenance : dépôt, chemin, branche, date de lecture
extrait_exemple()
```

## 8. Décisions validées par Émilien
(formulation exacte de l'accord et date, sinon « aucune »)

## 9. Problèmes rencontrés

## 10. Tests et résultats
(uniquement ce qui a réellement été exécuté, avec le résultat ; sinon « non testé »)

## 11. Prochaine action exacte
(et fichiers du Workspace à mettre à jour selon ChatGPT)
=== FIN DU PAQUET ===
````
~~~~~~

### Ce que fait Claude à la réception

1. Il vérifie que le paquet est complet et qu'il ne contient aucun secret ni donnée personnelle (sinon il n'intègre pas, prévient Émilien : [../SECURITE_ET_SECRETS.md](../SECURITE_ET_SECRETS.md)). Si les délimiteurs de bloc ont été altérés à la copie, les lignes `=== PAQUET DE TRANSFERT CHATGPT → CLAUDE ===` et `=== FIN DU PAQUET ===` font foi.
2. Il vérifie les statuts (aucune hypothèse promue en fait, aucune proposition promue en décision) et compare les fichiers et versions cités à l'état actuel de `main`.
3. Il place dans la section `[ChatGPT]` du journal du jour : (a) un **compte rendu synthétique en 11 sections** (partie 1), puis (b) le **paquet conservé intégralement**, tel que reçu, dans un bloc à quatre accents graves, sans rien résumer, supprimer ni reformuler (hypothèses, extraits de code et propositions non validées inclus). L'en-tête du paquet reste tel que reçu ; le statut courant est suivi dans [../AVANCEMENT.md](../AVANCEMENT.md) et [../CHANGELOG.md](../CHANGELOG.md). Il met à jour les fichiers concernés et note le paquet « EN ATTENTE D'INTÉGRATION » dans [../AVANCEMENT.md](../AVANCEMENT.md).
4. Il ouvre une PR (branche, un commit). Émilien fusionne.
5. Après fusion et relecture de `main` : statut INTÉGRÉ (ligne dans [../CHANGELOG.md](../CHANGELOG.md), retrait de la ligne d'attente).

Une analyse de ChatGPT n'est pas un correctif intégré tant que Claude ne l'a pas appliqué et testé.
