# INSERT INTO TABLE

Le code suivant permet d'insérer un jeu de données dans les tables.

_Note :je présente d'abord une requête d'insertion pour chaque table. Le code complet se trouve en bas de cette page._

__Table Agents:__
```sql
INSERT INTO agents VALUES (
    'NL521', 'Massamba', 'Beatrice', 'Conducteur', 'Exploitation', to_date('1980-12-03', 'YYYY-MM-DD'), 0752414587
);

select nom_agent, 
       matricule_agent, 
       to_char(date_naissance_Agent, 'DD/MM/YYYY') as date_nais
from agents;
```

__Table Usages__
```sql
INSERT INTO usages VALUES ('Travaux');
INSERT INTO usages VALUES ('Voyages');

SELECT * FROM usages;
```

__Table Moyens_roulants__
```sql
ALTER TABLE moyens_roulant MODIFY pmp_moyen_roul NUMBER;-- initialement de type 'date', le champ pmp_moyen_roulant est modifié en type 'number'

INSERT INTO moyens_roulant 
VALUES ('MP89CC', 'conduite conducteur', to_date('01-01-1997', 'DD-MM-YYYY'), to_date('1997-02-01', 'YYYY-MM-DD'), null, 150000, 'Voyages');

INSERT INTO moyens_roulant 
VALUES ('MP89CA', 'conduite automatique', to_date('01-01-1997', 'DD-MM-YYYY'), to_date('1997-02-01', 'YYYY-MM-DD'), null, 150000, 'Voyages');

SELECT * FROM moyens_roulant;
```

