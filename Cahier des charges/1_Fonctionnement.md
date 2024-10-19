# Fonctionnement

Note : cette partie contient des termes techniques.

Une moyen roulant (MR) métro, RER (réseau express régional) entre dans le parc dans le parc des actifs de l'entreprise. Un MR appartient à un Modèle et possède une numérotation unique. Exemple de modèle : MP 14 CA (Metro Pneu appel d'offres 2014). Un modèle est affecté à un ou plusieurs Ligne

Le code/identifiant d'un MR est composé du nom de modèle concatené au numéro unique.

Un MR est confié à un Agent conducteur (cas d'une conduite conducteur) : c'est la notion de Exploitation. A la fin d'une expoitation, le conducteur renseigne un "rapport d'exploitation" des informations sur le MR : kilométrage, heure de début et de fin d'exploitation.

Un MR doit être maintenu en bon état. Pour ce faire, il fait l'objet de deux types d'interventions : corrective et préventive.

1/ intervention corrective : après une exploitation, l'agent conducteur renseigne dans son rapport d'exploitation, les éventuelles avaries. En cas d'avaries/pannes, la table Interventions est mise à jour. Cette mise à jour se fait grâce à un trigger qui écoute le champ "avaries" de la table Exploitation.

2/ intervention préventive : après un certain kilométrage (15.000 Km dans le cas de métro), chaque MR doit faire l'objet d'une maintenance préventive. A l'atteinte du fameux nombre de kilomètres parcourus, la table Interventions est mise à jour. Cette mise à jour se fait grâce à un trigger qui écoute le champ "kilométrage" de la table Exploitation.

Dans les deux cas, le responsable/coordinateur des maintenances décide planifer une intervention. Il modifie l'état du MR (ex: indisponible) et renseigne ces informations : date de début (la date de fin et le compte-rendu seront renseingnés par les techniciens de maintenance), équipements concernés, Site (centre de dépannage ou atelier de maintenance), le ou les techniciens, la ou les Tâches à réalier.

Pour atteindre leur objectif de maintenance, les techniciens peuvent avoir besoin de Produits. Les produits sont stockés dans un Magasin. Un magasin se trouve sur un site.
