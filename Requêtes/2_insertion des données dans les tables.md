# INSERT INTO TABLE

Le code suivant permet d'insérer un jeu de données dans les tables.

_Note : je mets une une insertion par table. Le code plus complet se trouve en bas de cette page._

__Table Agents:__
```sql
INSERT INTO agents VALUES (
    'NL521', 'Massamba', 'Beatrice', 'Conducteur', 'Exploitation', to_date('1980-12-03', 'YYYY-MM-DD'), 0752414587
);
```
