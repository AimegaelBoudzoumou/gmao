# INSERT INTO produits_inseres

Rappel : lors de sa création, un produit a un stock réel (champ _qtite_reelle_produits_ dans la table _produits_) à nul (zéro).

Chaque insertion de produit (table _produits_inseres_) augemente le stock du produit en question.

Cette augmentation de stock est réalisée automatiquement, grâce à un _Trigger_

Ce _Trigger_ est déclenché lors d'une insertion dans la table _produits_inseres_

## Trigger et Insertion d'une données dans la table produits_inseres

```sql
-- ########################################### Create Trigger update_product_stock_after_inserting

CREATE OR REPLACE TRIGGER update_product_stock_after_inserting
AFTER INSERT ON produits_inseres
FOR EACH ROW
ENABLE
DECLARE
    
BEGIN
    UPDATE produits p
    SET qtite_reelle_produits = qtite_reelle_produits + :NEW.quantite_produits_inseres
    WHERE p.code_produits = :NEW.code_produits;
END;
/

-- ##############################################
DELETE FROM produits_inseres;
DELETE FROM produits;

select * from produits;
INSERT INTO produits VALUES ('PRTG8', 'Huile moteur', 'permet de maintenir le moteur en bon état',
                             'Type_P', 'Huile', 'Moteur', 'litre', 0, 25, TO_DATE('2000-06-11', 'YYYY-MM-DD'),
                             'non', 'MAG14'
                            );

SELECT * FROM produits_inseres;

SELECT * FROM  produits;

INSERT INTO produits_inseres(date_produits_inseres, quantite_produits_inseres, matricule_Agent, code_produits) 
       VALUES (TO_DATE(SYSDATE, 'DD-MM-YY'), 15, 'NL521', 'PRTG8');
SELECT * FROM produits_inseres;
SELECT * FROM produits;

INSERT INTO produits_inseres(date_produits_inseres, quantite_produits_inseres, matricule_Agent, code_produits) 
       VALUES (TO_DATE(SYSDATE, 'DD-MM-YY'), 30, 'NL521', 'PRTG8');
SELECT * FROM produits_inseres;
SELECT * FROM produits;
```
