# Cahier des charges - Spécifications fonctionnelles

## 1/ Historique-Fonctionnement

Note : cette partie contient des termes techniques.

Une moyen roulant (MR) métro, RER (réseau express régional) entre dans le parc dans le parc des actifs de l'entreprise. 
Un MR appartient à un __Modèle__ et possède une numérotation unique. 
Exemple de modèle : MP 14 CA (Metro Pneu appel d'offres 2014). Un modèle est affecté à un ou plusieurs __Ligne__

Le code/identifiant d'un MR est composé du nom de modèle concatené au numéro unique.

Un MR est confié à un __Agent__ conducteur (cas d'une conduite conducteur) : c'est la notion de __Exploitation__. 
A la fin d'une expoitation, le conducteur renseigne un "rapport d'exploitation" des informations sur le MR : kilométrage, heure de début et de fin d'exploitation.

Un MR doit être maintenu en bon état. Pour ce faire, il fait l'objet de deux types d'interventions : corrective et préventive.

1/ intervention corrective : après une exploitation, l'agent conducteur renseigne dans son rapport d'exploitation, les éventuelles avaries.
En cas d'avaries/pannes, la table __Interventions__ est mise à jour. Cette mise à jour se fait grâce à un _trigger_ qui écoute le champ "avaries" de la table Exploitation.

2/ intervention préventive : après un certain kilométrage (15.000 Km dans le cas de métro), chaque MR doit faire l'objet d'une maintenance préventive.
A l'atteinte du fameux nombre de kilomètres parcourus, la table __Interventions__ est mise à jour. Cette mise à jour se fait grâce à un _trigger_ qui écoute le champ "kilométrage" de la table Exploitation.

Dans les deux cas, le responsable/coordinateur des maintenances décide planifer une intervention. Il renseigne ces informations : date de début (la date de fin et le compte-rendu seront renseingnés par les techniciens de maintenance), équipements concernés, __Site__ (centre de dépannage ou atelier de maintenance), le ou les techniciens, la ou les __Tâches__ à réalier.

Pour atteindre leur objectif de maintenance, les techniciens peuvent avoir besoin de __Produits__. Les produits sont stockés dans un __Magasin__. Un magasin se trouve sur un site.

## 2/ Les entités et leurs attributs

### MR
code, mode de conduite (conduite conducteur cc ou conduite automatique ca), état (en service, en livraison, reformé, indisponible, sans affectation), modèle (exemples: _MP 89 CC_, _TMVI_), numéro (ex: _01_), usage (travaux, voyageurs), 

### Modèle de MR
constructeur, composition, écartement des roues, longueur, intercirculation, vitesse maximale, affectation actuelle, livraison, période de service, équipement

### Ligne
numéro

### Equipement
nom, MR associé

### Agent/Employé
nom, prenom, role, département (MRF ou uExpoitation), date de naissance, téléphone

### Exploitation
date, heure début, heure fin, kilométrage, avaries, compte-rendu agent exploitant, lieu où la l'avariee est constatée, niveau de gravité de l'avarie,

### Interventions
date début, date fin, équipement

### Site
type (soit "atelier de maintenance" pour la maintenance préventive, soit "centre de dépannage" pour la maintenance corrective), adresse, responsable

### Tâches
nom, intervention concernées

### Produits
nom, descriptif, unité de comptage, quantité réelle, seuil limite, gamme, catégorie, date du premier enregistrement

### Magasins
nom, adresse, 

### Quelques piste de réflexions :
- est ce qu'une ligne peut accueillir des modèle de MR différents ?
