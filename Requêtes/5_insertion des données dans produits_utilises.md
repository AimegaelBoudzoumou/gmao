# INSERT INTO produits_utilises

Chaque sortie de produit (table produits_utilises) diminue le stock du produit en question.

Cette diminution de stock est réalisée automatiquement, grâce à un Trigger.

Ce Trigger est déclenché lors d'une insertion dans la table produits_utilises:
- point 1: le _Trigger_ vérifie que la quantité à sortir est inférieure ou égale au stock réel (qtite_reelle_produits dans la table produits).
- point 2: si le point 1 est vérifié (vrai), alors le stock réel ((qtite_reelle_produits dans la table produits)) est mis à jour

## Trigger et Insertion d'une données dans la table produits_utilises
