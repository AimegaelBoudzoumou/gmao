```sql
DROP TABLE IF EXISTS employes;

CREATE TABLE employes (
    idValue NUMBER GENERATED BY DEFAULT AS IDENTITY,
    matricule VARCHAR2(50),
    nom VARCHAR2(50),
    prenom VARCHAR2(50),
    full_name VARCHAR2(150) GENERATED ALWAYS AS (
    	prenom || ' ' || nom    
    ),
    PRIMARY KEY(matricule)
);
INSERT INTO employes(matricule, nom, prenom) VALUES ('JJKL25', 'Louzolo', 'Judicaelle');
SELECT * FROM employes;
/*
Example : SYSDATE
INSERT INTO produits_utilises(date_produits_utilises, quantite_produits_utilises, code_produits, code_interventions) 
       VALUES (TO_DATE(SYSDATE, 'DD-MM-YY'), 1, 'PRTG8', 'JHJU25');

Example : TO_CHAR
SELECT nom_agent, 
       matricule_agent, 
       TO_CHAR(date_naissance_Agent, 'DD/MM/YYYY') as date_nais
FROM agents;
*/
```


```python
list_fruits = ['banana', 'mango', 'papaya']
for fruit in list_fruits:
  print(fruit)
```
