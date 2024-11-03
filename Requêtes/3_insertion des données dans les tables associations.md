# INSERT INTO TABLE (2/2)

Le code suivant permet d'insérer un jeu de données dans les tables_associations. Dans un autre fichier, j'ai rédigé le code SQL d'insertion des données dans les tables _propres_.

_Note : je présente d'abord une requête d'insertion pour chaque table. Le code complet se trouve en bas de cette page._

__Table bon_de_missions__
```sql
INSERT INTO bon_de_missions VALUES (TO_DATE(CURRENT_DATE, 'yyyy-MM-DD'), 'NL521', 'JHJU25');
```
__Table historique_statuts__

__Table Concerner__

__Table Taches_effectuees__

__Table Produits inseres__

Ecrire un Trigger qui met à jour la table produit, quand un produit est inséré

__Table Produits utilises__

Ecrire un Trigger qui met à jour la table produit, quand un produit est utilisé

## Code complet
```sql
-- bon_de_missions
INSERT INTO bon_de_missions VALUES (to_date(CURRENT_DATE, 'yyyy-MM-DD'), 'NL521', 'JHJU25');

```


