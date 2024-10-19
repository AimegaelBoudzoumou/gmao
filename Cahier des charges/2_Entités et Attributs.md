# Entités et Attributs

L'analyse du cahier des charges et des spécifications fonctionnelles permet de répérer les éléments (entités) amenés à interagir au sein d'un applicatif.
Chaque entité contient des attributs. Les entités sont reliées entre elles par des associations.

Plus tard, chaque entité sera représentée par une table dans la base de données; et les attributs seront les champs de ces tables.

<!--Ce tutoriel de IBM contient des informations détaillées sur le modèle relationnel: 
[data-modeling](https://www.ibm.com/fr-fr/topics/data-modeling)-->

## MR (pour Moyen Roulant)
code (concaténation de plusieurs informations), matériel (exemples: MP 89 CC, TMVI), livraison, mode de conduite (conduite conducteur cc ou conduite automatique ca), livré, autres informations, statut (en service, en livraison, reformé, indisponible, sans affectation), usage (travaux, voyageurs)

## Matériel
constructeur, composition, écartement des roues, longueur, intercirculation, vitesse maximale, affectation actuelle, livraison, période de service, équipement

## Ligne
numéro

## Equipement
nom, MR associé

## Agent/Employé
nom, prenom, role, département (MRF ou uExpoitation), date de naissance, téléphone

## Exploitation
date, heure début, heure fin, kilométrage, avaries, compte-rendu agent exploitant, lieu où la l'avariee est constatée, niveau de gravité de l'avarie,

## Interventions
date début, date fin, équipement

## Site
type (soit "atelier de maintenance" pour la maintenance préventive, soit "centre de dépannage" pour la maintenance corrective), adresse, responsable

## Tâches
nom, intervention concernées

## Produits
nom, descriptif, unité de comptage, quantité réelle, seuil limite, gamme, catégorie, date du premier enregistrement

## Magasins
nom, adresse,

### Quelques piste de réflexions :
- est ce qu'une ligne peut accueillir des modèle de MR différents ?
