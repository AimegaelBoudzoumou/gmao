# INSERT INTO TABLE

Le code suivant permet d'insérer un jeu de données dans les tables _propres_.
Dans un autre fichier, j'ai rédigé le code SQL d'insertion des données dans les tables-associations.

_Note : je présente d'abord une requête d'insertion pour chaque table. Le code complet se trouve en bas de cette page._

__Table agents:__
```sql
INSERT INTO agents VALUES (
    'NL521', 'Massamba', 'Beatrice', 'Conducteur', 'Exploitation', to_date('1980-12-03', 'YYYY-MM-DD'), 0752414587
);

SELECT nom_agent, 
       matricule_agent, 
       TO_CHAR(date_naissance_Agent, 'DD/MM/YYYY') as date_nais
FROM agents;
```

__Table usages__
```sql
INSERT INTO usages VALUES ('Travaux');
INSERT INTO usages VALUES ('Voyages');
```

__Table moyens_roulants__
```sql
INSERT INTO moyens_roulant 
VALUES ('MP89CC', 'conduite conducteur', to_date('01-01-1997', 'DD-MM-YYYY'), to_date('1997-02-01', 'YYYY-MM-DD'), null, 150000, 'Voyages');

INSERT INTO moyens_roulant 
VALUES ('MP89CA', 'conduite automatique', to_date('01-01-1997', 'DD-MM-YYYY'), to_date('1997-02-01', 'YYYY-MM-DD'), null, 150000, 'Voyages');
```

__Table equipements__
```sql
INSERT INTO equipements VALUES ('BG452', 'Boggie', 'MP89CC');
INSERT INTO equipements VALUES ('LP4512', 'Lampe', 'MP89CA');
```

__Table statuts__
```sql
INSERT INTO statuts VALUES ('En service');
INSERT INTO statuts VALUES ('En reparation');
```

__Table sites__
```sql
-- Atelier du métro de Paris : https://fr.wikipedia.org/wiki/Ateliers_du_m%C3%A9tro_de_Paris

INSERT INTO sites VALUES ('CDT-Fontenay',
                          'Fontenay AMT L.1 et AMP ', 
                          'centre de dépannage', 
                          '16, rue J.J. Rousseau 94120 Fontenay-sous-Bois', 
                          '48° 50′ 51″ nord, 2° 27′ 27″ est',
                          0154856232,
                          'Beranger'
);

INSERT INTO sites VALUES ('AMT-Mallot',
                          'Maillot AMT L.1 ', 
                          'atelier de maintenance', 
                          'Place de la Porte-Maillot 75017 Paris', 
                          '48° 52′ 38″ nord, 2° 17′ 03″ est',
                          0154856254,
                          'Moussawi'
);
```

__Table magasins__
```sql
-- il peut être pertinent de supprimer le champ 'adresse_magasins' de la table magasin, car le champ site nous fournit déjà une adresse
INSERT INTO magasins VALUES ('MAG14', 'magasin Fontenay', 'Fontenay', 'CDT-Fontenay');
INSERT INTO magasins VALUES ('MAG48', 'magasin Maillot', 'Maillot', 'AMT-Mallot');
```

__Table produits__
```sql
select * from produits;
INSERT INTO produits VALUES ('PRTG8', 'Huile moteur', 'permet de maintenir le moteur en bon état',
                             'Type_P', 'Huile', 'Moteur', 'litre', 0, 25, to_date('2000-06-11', 'YYYY-MM-DD'),
                             'non', 'MAG14');
```

__Table Taches__
```sql
INSERT INTO taches VALUES ('CH-HU', 'changement huile');
```

__Table interventions__
```sql
INSERT INTO interventions VALUES ('JHJU25', to_date('2024-11-04', 'YYYY-MM-DD'), null, 'préventive', null, 'MP89CA', 'AMT-Mallot');
```

# code complet

```sql
-- Table agents

INSERT INTO agents VALUES (
    'NL521', 'Massamba', 'Beatrice', 'Conducteur', 'Exploitation', to_date('1980-12-03', 'YYYY-MM-DD'), 0752414587
);

/*SELECT nom_agent, 
       matricule_agent, 
       to_char(date_naissance_Agent, 'DD/MM/YYYY') as date_nais
FROM agents;*/

-- Table usages
INSERT INTO usages VALUES ('Travaux');
INSERT INTO usages VALUES ('Voyages');

-- Table moyens_roulant
INSERT INTO moyens_roulant 
VALUES ('MP89CC', 'conduite conducteur', to_date('01-01-1997', 'DD-MM-YYYY'), to_date('1997-02-01', 'YYYY-MM-DD'), null, 150000, 'Voyages');

INSERT INTO moyens_roulant 
VALUES ('MP89CA', 'conduite automatique', to_date('01-01-1997', 'DD-MM-YYYY'), to_date('1997-02-01', 'YYYY-MM-DD'), null, 150000, 'Voyages');

-- Table equipements
INSERT INTO equipements VALUES ('BG452', 'Boggie', 'MP89CC');
INSERT INTO equipements VALUES ('LP4512', 'Lampe', 'MP89CA');

-- Table statuts
INSERT INTO statuts VALUES ('En service');
INSERT INTO statuts VALUES ('En reparation');

-- Table sites
INSERT INTO sites VALUES ('CDT-Fontenay',
                          'Fontenay AMT L.1 et AMP ', 
                          'centre de dépannage', 
                          '16, rue J.J. Rousseau 94120 Fontenay-sous-Bois', 
                          '48° 50′ 51″ nord, 2° 27′ 27″ est',
                          0154856232,
                          'Beranger'
);

INSERT INTO sites VALUES ('AMT-Mallot',
                          'Maillot AMT L.1 ', 
                          'atelier de maintenance', 
                          'Place de la Porte-Maillot 75017 Paris', 
                          '48° 52′ 38″ nord, 2° 17′ 03″ est',
                          0154856254,
                          'Moussawi'
);

-- Table magasins
INSERT INTO magasins VALUES ('MAG14', 'magasin Fontenay', 'Fontenay', 'CDT-Fontenay');
INSERT INTO magasins VALUES ('MAG48', 'magasin Maillot', 'Maillot', 'AMT-Mallot');

-- Table produits

INSERT INTO produits VALUES ('PRTG8', 'Huile moteur', 'permet de maintenir le moteur en bon état',
                             'Type_P', 'Huile', 'Moteur', 'litre', 0, 25, to_date('2000-06-11', 'YYYY-MM-DD'),
                             'non', 'MAG14'
);

-- Table Taches
INSERT INTO taches VALUES ('CH-HU', 'changement huile');

-- Table interventions
INSERT INTO interventions VALUES ('JHJU25', to_date('2024-11-04', 'YYYY-MM-DD'), null, 'préventive', null, 'MP89CA', 'AMT-Mallot');
```
