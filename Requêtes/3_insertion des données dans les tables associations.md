# INSERT INTO TABLE (2/2)

Le code suivant permet d'insérer un jeu de données dans les tables_associations. Dans un autre fichier, j'ai rédigé le code SQL d'insertion des données dans les tables _propres_.

_Note : je présente d'abord une requête d'insertion pour chaque table. Le code complet se trouve en bas de cette page._

__Table bon_de_missions__
```sql
INSERT INTO bon_de_missions VALUES (TO_DATE(SYSDATE, 'DD-MM-YY'), 'NL521', 'JHJU25');

-- SELECT TO_CHAR(date_bon_de_missions, 'DD-MM-YYYY') as date_bon_missions, matricule_agent, code_interventions FROM bon_de_missions;
```
__Table historique_statuts__
```SQL
INSERT INTO historique_statuts VALUES (TO_DATE(SYSDATE, 'DD-MM-YY'), 'MP89CC', 'En service');

-- SELECT code_moyen_roulant, nom_statuts, TO_CHAR(date_historique_statuts, 'DD-MM-YYYY') as date_histo FROM historique_statuts;
```

__Table Concerner__
```sql
INSERT INTO concerner VALUES (TO_DATE(SYSDATE, 'DD-MM-YY'), 'JHJU25', 'BG452');

-- SELECT code_interventions, code_equipements, TO_CHAR(date_concerner, 'DD-MM-YYYY') as date_concerner FROM concerner;
```

__Table Taches_effectuees__
```sql
INSERT INTO taches_effectuees VALUES ('JHJU25', 'CH-HU');
```

__Table Produits inseres__

Ecrire un Trigger qui met à jour la table produit, quand un produit est inséré

__Table Produits utilises__

Ecrire un Trigger qui met à jour la table produit, quand un produit est utilisé

## Code complet
```sql

-- bon_de_missions
INSERT INTO bon_de_missions VALUES (TO_DATE(SYSDATE, 'DD-MM-YY'), 'NL521', 'JHJU25');

-- Table historique_statuts
INSERT INTO historique_statuts VALUES (TO_DATE(SYSDATE, 'DD-MM-YY'), 'MP89CC', 'En service');

-- Table Concerner
INSERT INTO concerner VALUES (TO_DATE(SYSDATE, 'DD-MM-YY'), 'JHJU25', 'BG452');

-- Table Taches_effectuees
INSERT INTO taches_effectuees VALUES ('JHJU25', 'CH-HU');

```
