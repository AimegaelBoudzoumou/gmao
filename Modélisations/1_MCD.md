# MCD
__Note__ : Ce tutoriel de IBM contient des informations détaillées sur la [modélisation des données](https://www.ibm.com/fr-fr/topics/data-modeling)

Une explication du MCD (modèle conceptuel de données) se trouve en bas de la page en cours.

Outil utilisé: logiciel __AnalyseSI__ en environnement __Ubuntu 18.04.5 LTS__

![mcd_gmao_v1](https://github.com/user-attachments/assets/9a3a7ef2-a165-4cea-ada7-ffaf1a2ea1c7)

## Explication des principales entités du MCD ci-dessus:

__1/ moyens roulant__ : il s'agit d'un métro, rer, tram. 

Un moyen roulant :
- peut faire l'objet d'aucune ou plusieurs pannes
-  peut se voir affecter, pour exploitation, au moins un agent
-  peut être équipé de plusieurs équipements

__2/ interventions__ : il s'agit de l'entité qui permet de planifier un intervention sur un moyen roulant. 

Un intervention:
- est l'acte de réparer un et seul moyen roulant
- fait l'objet d'au moins une tâche
- peut concerner plusieurs équipements
- fait l'objet d'un bon de mission pour au moins un agent
- peut faire l'objet de l'utilisation d'aucun ou plusieurs produits
- se déroule dans un site précis

__3/ agents__: il s'agit soit d'un employé du département MRF (moyens roulant férroviaire) soit d'un agent de département exploitation (chauffeur). 

Un agent:
- peut insérer des produits dans le logiciel (cette incombe plus aux agents MRF)
- peut recevoir plusieurs bons de mission (cette incombe plus aux agents MRF)
- peut se voir confier pour exploitation, plusieurs moyens roulant (cette incombe plus aux agents de l'exploitation)

__4/ sites__: c'est le lieu où se déroule une intervention. 

Un site:
- peut accueillir plusieurs interventions
- peut accueillir aucun ou plusieurs magasins

__Note__ : 

Dans le MCD ci-dessus, il peut être pertinent d'ajouter une entité "materiel". 

Cette dernière serait reliée à l'entité "moyen_roulant"; via une association "appartenir" ayant les cardinalités 1,1 (pour moyen_roulant) et 0,N ou 1,N (pour materiel).


