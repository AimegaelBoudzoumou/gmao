# INSERT INTO produits_utilises

Chaque sortie de produit (table produits_utilises) diminue le stock du produit en question.

Cette diminution de stock est réalisée automatiquement, grâce à un Trigger.

Ce Trigger est déclenché lors d'une insertion dans la table produits_utilises:
- point 1: le _Trigger_ vérifie que la quantité à sortir est inférieure ou égale au stock réel (_qtite_reelle_produits_ dans la table _produits_).
- point 2: si le point 1 est vérifié (vrai), alors le stock réel (champ _qtite_reelle_produits_ dans la table _produits_) est mis à jour

## Trigger et Insertion d'une données dans la table produits_utilises
```sql
-- ######################################## Create Trigger trg_before_inserting_on_produits_utilises

CREATE OR REPLACE TRIGGER trg_before_inserting_on_produits_utilises
BEFORE INSERT ON produits_utilises
FOR EACH ROW
ENABLE
-- WHEN ...
DECLARE
    qtite_reelle_produits_en_bd produits.qtite_reelle_produits%TYPE;
BEGIN
    SELECT qtite_reelle_produits INTO qtite_reelle_produits_en_bd FROM produits p WHERE p.code_produits = :NEW.code_produits;

	IF (:NEW.quantite_produits_utilises <= qtite_reelle_produits_en_bd AND
        :NEW.quantite_produits_utilises > 0 ) THEN
        	UPDATE produits p
      		SET    qtite_reelle_produits = qtite_reelle_produits - :NEW.quantite_produits_utilises
        	WHERE  p.code_produits = :NEW.code_produits;
	ELSE
        raise_application_error(-20130, 'Veuillez saisir un nombre égal ou inférieur au stock réel: ' || qtite_reelle_produits_en_bd);
	END IF;
END;
/

-- ######################################## Manipulation

INSERT INTO produits_utilises(date_produits_utilises, quantite_produits_utilises, code_produits, code_interventions) 
       VALUES (TO_DATE(SYSDATE, 'DD-MM-YY'), 1, 'PRTG8', 'JHJU25');

SELECT * FROM produits_utilises ORDER BY produit_utilise_id;
SELECT * FROM produits;
```
