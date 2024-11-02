# INSERT INTO TABLE

Le code suivant permet d'insérer un jeu de données dans les tables_associations. Dans un autre fichier, j'ai rédigé le code SQL d'insertion des données dans les tables _propres_.

_Note : je présente d'abord une requête d'insertion pour chaque table. Le code complet se trouve en bas de cette page._

__Table bon_de_missions__
```sql
INSERT INTO bon_de_missions VALUES (to_date(CURRENT_DATE, 'yyy-MM-DD'), 'NL521', 'JHJU25');
```

__Table historique_statuts__


__Table Concerner__



## Code complet
```sql
-- bon_de_missions
INSERT INTO bon_de_missions VALUES (to_date(CURRENT_DATE, 'yyy-MM-DD'), 'NL521', 'JHJU25');

```


