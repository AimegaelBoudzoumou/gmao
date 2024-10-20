# Fonctionnement

Le texte qui suit représente le cahier des charges et les spécifications fonctionnelles de ce système de GMAO.

__Note :__
- ce texte contient des termes techniques.
- les mots en gras représentent les principales entités.

## __A/ Exploitation__

Une moyen roulant (__MR__) métro, RER (réseau express régional) est intégré dans le parc des actifs de l'entreprise. 

Un MR appartient à un __matériel__ et possède un code unique. Un matériel est affecté à une ou plusieurs __lignes__.

Le code/identifiant unique d'un MR est le résultat de la concaténation de plusieurs informations:

Exemple de code : MP 14 CA n°1001

Matériel : MP 14 CA VA. Metro Pneu appel d'offres 2014 Conduite Automatique Série VA à 8 voitures

Numéro : 1001 (CA-07)

Un MR est confié à un __Agent conducteur__ (cas d'une conduite conducteur dite CC) : c'est la notion d'__exploitation__.

Dans le cas d'une conduite automatique (dite CA), l'attribut Agent de la table "exploitation" contient une valeur par défaut (exemple Automatique).

A la fin d'une exploitation, le conducteur renseigne un "rapport d'exploitation" des informations sur le MR : kilométrage, heure de début et de fin d'exploitation. Dans le cas d'une CA (Conduite Automatique), ces informations sont soit copiées manuellemen par un agent, soit transmise informatique par le MR à la base de données.

## __B/ Maintenance__: cas d'une CC (conduite conducteur)

Un MR doit être maintenu en bon état. Pour ce faire, il fait l'objet de deux types d'__interventions__ : corrective et préventive.

__1/ intervention corrective__ : après une exploitation, l'agent conducteur renseigne dans son rapport d'exploitation, les éventuelles __avaries__. En cas d'avaries/pannes, la table interventions est mise à jour. Cette mise à jour se fait grâce à un _**trigger**_ qui écoute le champ "avaries" de la table exploitation.

__2/ intervention préventive__ : après un certain kilométrage (15.000 Km dans le cas de métro), chaque MR doit faire l'objet d'une maintenance préventive. A l'atteinte du fameux nombre de kilomètres parcourus, la table interventions est mise à jour. Cette mise à jour se fait grâce à un _**trigger**_ qui écoute le champ "PMP" (pour Prochaine Maintenance Préventive). de la table MR (ou Exploitation : à décider).

Fonctionnellement : le champ MR.PMP (le champ PMP de la table MR) vaut initialement 15.000. Chaque fois que le champ "kilométrage" de la table Exploitation est mis à jour, le contrôle suivant est effectué :

Si Exploitation.Kilometrage >= MR.PMP alors : les deux actions suivantes sont à effectuer :
- le MR est enregistré dans la table "interventions" pour une maintenance préventive.
- le champ MR.PMP est incrémenté de 15.000 (représentant ainsi le prochaine kilométrage afin de planifier la prochaine maintenance préventive).

Dans la même logique, un __**trigger**__ similaire peut être mis en place pour planifer le "changement des pneus de métro", qui doit se faire chaque 250.000 Km environ.


Dans les deux types d'intervention (préventive ou corrective), le responsable/coordinateur des maintenances décide de planifer une intervention. Il modifie l'état du MR et renseigne ces informations : date de début (la date de fin et le compte-rendu seront renseignés par les techniciens de maintenance), __équipements__ concernés, __site__ (centre de dépannage ou atelier de maintenance), le ou les techniciens en charge de la maintenance, la ou les __tâches__ à réaliser.

## __C/ Stocks__

Pour atteindre leur objectif de maintenance, les techniciens peuvent avoir besoin de __produits__. Les produits sont stockés dans un __magasin__. Un magasin se trouve sur un site.

Chaque entrée d'un produit augmente la quantité réelle du produit. Chaque sortie (utilisation lors d'une intervention) de produit diminue la quantité réelle du produit.

Il est possible de mettre en place un __**trigger**__ pour optimiser le stock des produits. Ce _triger_ écoutera le champ "seuil alerte" de la table "produits". En fonction du type, gamme et catégorie du produit, si la quatité réelle est inférieur au seuil alerte, alors une champ "alerte_produit" de type varchar est mis à _oui_ (ce champ vaut initialement _non_).

Si on souhaite garder un historique des alertes produits, on doit créer une table (par exemple __alerte_produits__) associée à la table produit. Les cardinalités max de l'association vaudront N,N

## __D/ Quelques points à éclaircir__ :
- est ce qu'une ligne peut accueillir des matériels différents ?
- est ce que tout un matériel est affecté uniquement à une seule ligne ?
- est-il pertinent de créer une table "type_de_maintenance" qui serait reliée aux tables "interventions" et "sites" ?
