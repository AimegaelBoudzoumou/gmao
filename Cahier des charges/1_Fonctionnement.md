# Fonctionnement

Le texte qui suit représente le cahier des charges et les spécifications fonctionnelles de ce système de GMAO.

__Note :__
- ce texte contient des termes techniques.
- les mots en gras représentent les principales entités.

Une moyen roulant (__MR__) métro, RER (réseau express régional) entre dans le parc des actifs de l'entreprise. 
Un MR appartient à un __matériel__ et possède un code unique.
Un modèle est affecté à une ou plusieurs __lignes__.

Le code/identifiant unique d'un MR est le résultat de la concaténation de plusieurs informations:

Exemple de code : MP 14 CA n°1001

Matériel : MP 14 CA VA. Metro Pneu appel d'offres 2014 Conduite Automatique Série VA à 8 voitures

Numéro : 1001 (CA-07)

Un MR est confié à un __Agent conducteur__ (cas d'une conduite conducteur) : c'est la notion d'__exploitation__. A la fin d'une expoitation, le conducteur renseigne un "rapport d'exploitation" des informations sur le MR : kilométrage, heure de début et de fin d'exploitation.

Un MR doit être maintenu en bon état. Pour ce faire, il fait l'objet de deux types d'__interventions__ : corrective et préventive.

__1/ intervention corrective__ : après une exploitation, l'agent conducteur renseigne dans son rapport d'exploitation, les éventuelles __avaries__. En cas d'avaries/pannes, la table Interventions est mise à jour. Cette mise à jour se fait grâce à un _trigger_ qui écoute le champ "avaries" de la table exploitation.

__2/ intervention préventive__ : après un certain kilométrage (15.000 Km dans le cas de métro), chaque MR doit faire l'objet d'une maintenance préventive. A l'atteinte du fameux nombre de kilomètres parcourus, la table interventions est mise à jour. Cette mise à jour se fait grâce à un _trigger_ qui écoute le champ "PMP" (pour Prochaine Maintenance Préventive). de la table MR (ou Exploitation : à décider).

Fonctionnellement : le champ "PMP" vaut initialement 15.000. Chaque fois que le champ "kilométrage" de la table Exploitation est mis à jour, le contrôle suivant est effectué :

Si Exploitation.Kilometrage >= MR.PMP alors : les deux actions suivantes sont à effectuer :
- le MR est enregistré dans la table "interventions" pour une maintenance préventive.
- le champ MR.PMP est incrémenté de 15.000 (représentant ainsi le prochaine kilométrage afin de planifier la prochaine maintenance préventive).

Dans la même logique, un _trigger_ similaire peut être mis en place pour planifer le "changement des pneus de métro", qui doit se faire chaque 250.000 Km environ.


Dans les deux types d'intervention (préventive ou corrective), le responsable/coordinateur des maintenances décide de planifer une intervention. Il modifie l'état du MR et renseigne ces informations : date de début (la date de fin et le compte-rendu seront renseignés par les techniciens de maintenance), __équipements__ concernés, __site__ (centre de dépannage ou atelier de maintenance), le ou les techniciens en charge de la maintenance, la ou les __tâches__ à réaliser.

Pour atteindre leur objectif de maintenance, les techniciens peuvent avoir besoin de __produits__. Les produits sont stockés dans un __magasin__. Un magasin se trouve sur un site.

### Quelques questions à éclaircir :
- est ce qu'une ligne peut accueillir des matériel de MR différents ?
- est ce que tout le matériel est affecté uniquement à une seule ligne ?
