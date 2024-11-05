# INSERT INTO produits_utilises

Chaque sortie de produit (table produits_utilises) diminue le stock du produit en question.

Cette diminution de stock est réalisée automatiquement, grâce à un Trigger.

Ce Trigger est déclenché lors d'une insertion dans la table produits_utilises:
- point 1: le _Trigger_ vérifie que la quantité à sortir est inférieure ou égale au stock réel (qtite_reelle_produits dans la table produits).
- point 2: si le point 1 est vérifié (vrai), alors le stock réel (qtite_reelle_produits dans la table produits) est mis à jour

## Trigger et Insertion d'une données dans la table produits_utilises -- A TESTER
```sql
DELETE FROM produits_utilises;
DELETE FROM produits_inseres;
DELETE FROM produits;

INSERT INTO produits VALUES ('PRTG8', 'Huile moteur', 'permet de maintenir le moteur en bon état',
                             'Type_P', 'Huile', 'Moteur', 'litre', 0, 25, TO_DATE('2000-06-11', 'YYYY-MM-DD'),
                             'non', 'MAG14'
                            );
INSERT INTO produits_inseres(date_produits_inseres, quantite_produits_inseres, matricule_Agent, code_produits) 
       VALUES (TO_DATE(SYSDATE, 'DD-MM-YY'), 12, 'NL521', 'PRTG8');

SELECT * FROM produits_inseres;

CREATE OR REPLACE TRIGGER update_product_stock_after_using
AFTER INSERT ON produits_utilises
FOR EACH ROW
ENABLE
	WHEN (NEW.quantite_produits_utilises <= qtite_reelle_produits)
DECLARE
    qtite_reelle_produits produits.qtite_reelle_produits%TYPE;
	produit_utilise_id    produits_utilises.produit_utilise_id%TYPE;	
BEGIN
    SELECT qtite_reelle_produits INTO qtite_reelle_produits FROM produits p WHERE p.code_produits = :NEW.code_produits;

    IF :NEW.quantite_produits_utilises <= qtite_reelle_produits THEN -- quantite_produits_utilises
      UPDATE produits p
      SET    p.qtite_reelle_produits = p.qtite_reelle_produits - :NEW.quantite_produits_utilises
      WHERE  p.code_produits = :NEW.code_produits;
	ELSE
        DELETE FROM produits_inseres;-- WHERE produit_utilise_id = :NEW.produit_utilise_id;
    	DBMS_OUTPUT.PUT_LINE('Impossible utiliser ce produit. Problème de stock');	  
    END IF;
END;
/

INSERT INTO produits_utilises(date_produits_utilises, quantite_produits_utilises, code_produits, code_interventions) 
       VALUES (TO_DATE(SYSDATE, 'DD-MM-YY'), 12, 'PRTG8', 'JHJU25');
SELECT * FROM produits_utilises;
SELECT * FROM produits;

INSERT INTO produits_utilises(date_produits_utilises, quantite_produits_utilises, code_produits, code_interventions) 
       VALUES (TO_DATE(SYSDATE, 'DD-MM-YY'), 1, 'PRTG8', 'JHJU25');
SELECT * FROM produits_utilises;
SELECT * FROM produits;

```
