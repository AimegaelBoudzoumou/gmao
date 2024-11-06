# INSERT INTO produits_utilises

Chaque sortie de produit (table produits_utilises) diminue le stock du produit en question.

Cette diminution de stock est réalisée automatiquement, grâce à un Trigger.

Ce Trigger est déclenché lors d'une insertion dans la table produits_utilises:
- point 1: le _Trigger_ vérifie que la quantité à sortir est inférieure ou égale au stock réel (qtite_reelle_produits dans la table produits).
- point 2: si le point 1 est vérifié (vrai), alors le stock réel (qtite_reelle_produits dans la table produits) est mis à jour

## Trigger et Insertion d'une données dans la table produits_utilises -- A TESTER
```sql
CREATE OR REPLACE TRIGGER trg_before_inserting_on_produits_utilises
BEFORE INSERT ON produits_utilises
FOR EACH ROW
ENABLE
	--WHEN (NEW.quantite_produits_utilises <= qtite_reelle_produits)
DECLARE
    qtite_reelle_produits_en_bd produits.qtite_reelle_produits%TYPE;
	--produit_utilise_id    produits_utilises.produit_utilise_id%TYPE;	
BEGIN
    SELECT qtite_reelle_produits INTO qtite_reelle_produits_en_bd FROM produits p WHERE p.code_produits = :NEW.code_produits;

    IF :NEW.quantite_produits_utilises > qtite_reelle_produits_en_bd THEN
        --DBMS_OUTPUT.PUT_LINE('Stock insuffisant');
		raise_application_error(-20110,'Stock insuffisant');
	ELSE
        UPDATE produits p
      	SET    qtite_reelle_produits = qtite_reelle_produits - :NEW.quantite_produits_utilises
        WHERE  p.code_produits = :NEW.code_produits;
	END IF;
END;
/
    
-- ######################################## Manipulation

INSERT INTO produits VALUES ('PRTG8', 'Huile moteur', 'permet de maintenir le moteur en bon état',
                             'Type_P', 'Huile', 'Moteur', 'litre', 0, 25, TO_DATE('2000-06-11', 'YYYY-MM-DD'),
                             'non', 'MAG14'
                            );
INSERT INTO produits_inseres(date_produits_inseres, quantite_produits_inseres, matricule_Agent, code_produits) 
       VALUES (TO_DATE(SYSDATE, 'DD-MM-YY'), 8, 'NL521', 'PRTG8');

INSERT INTO produits_utilises(date_produits_utilises, quantite_produits_utilises, code_produits, code_interventions) 
       VALUES (TO_DATE(SYSDATE, 'DD-MM-YY'), 9, 'PRTG8', 'JHJU25');

SELECT * FROM produits_utilises;
SELECT * FROM produits;
```
