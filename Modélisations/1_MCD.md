# MCD
Une explication du MCD se trouve en bas de la page en cours

Ce tutoriel de IBM contient des informations détaillées sur la [modélisation des données](https://www.ibm.com/fr-fr/topics/data-modeling)

![mcd_gmao_v1](https://github.com/user-attachments/assets/93205b95-f030-4609-809d-3a3502204650)

## Explication des principales entités du MCD ci-dessus:

__moyens roulant__ : il s'agit d'un métro, rer, tram. Un moyen roulant :
- peut faire l'objet d'aucune ou plusieurs pannes
-  peut se voir affecter, pour exploitation, au moins un agent
-  peut être équipé de plusieurs équipements

__interventions__ : il s'agit de l'entité qui permet de planifier un intervention sur un moyen roulant. Un intervention:
- est l'acte de réparer un et seul moyen roulant
- fait l'objet d'au moins une tâche
- peut concerner plusieurs équipements
- fait l'objet d'un bon de mission pour au moins un agent
- peut faire l'objet de l'utilisation d'aucun ou plusieurs produits
- se déroule dans un site précis

__agents__: il s'agit soit d'un employé du département MRF (moyens roulant férroviaire) soit d'un agent de département exploitation (chauffeur). Un agent:
- peut insérer des produits dans le logiciel (cette incombe plus aux agents MRF)
- peut recevoir plusieurs bons de mission (cette incombe plus aux agents MRF)
- peut se voir confier pour exploitation, plusieurs moyens roulant (cette incombe plus aux agents de l'exploitation)

__sites__: c'est le lieu où se déroule une intervention. Un site:
- peut accueillir plusieurs interventions
- peut accueillir aucun ou plusieurs magasins




