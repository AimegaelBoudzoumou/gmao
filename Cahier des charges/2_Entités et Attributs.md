# Entités et Attributs

L'analyse du cahier des charges et des spécifications fonctionnelles permet de répérer les éléments (entités) amenés à interagir au sein d'un applicatif.
Chaque entité contient des attributs. Les entités sont reliées entre elles par des associations.

Plus tard, chaque entité sera représentée par une table dans la base de données; et les attributs seront les champs de ces tables.

<!--Ce tutoriel de IBM contient des informations détaillées sur le modèle relationnel: 
[data-modeling](https://www.ibm.com/fr-fr/topics/data-modeling)-->

## MR (pour Moyen Roulant)
code (concaténation de plusieurs informations), matériel (exemples: MP 89 CC, TMVI), livraison, conduite (conduite conducteur cc ou conduite automatique ca), livré, autres informations, statut (en service, en livraison, reformé, indisponible, sans affectation), usage (travaux, voyageurs), arrivée, mise en service, départ, PMP (Prochaine Maintenance Préventive)

## Matériel
code, constructeur, composition, écartement des roues, longueur, intercirculation, vitesse maximale, affectation actuelle, livraison, période de service, équipement

## Ligne
numéro

## Equipement
nom, MR associé

## Agent/Employé
nom, prenom, poste, département (MRF ou Expoitation), date de naissance, téléphone

## Exploitation
agent, date, heure début, heure fin, kilométrage, avaries, compte-rendu agent exploitant, lieu où la l'avariee est constatée, niveau de gravité de l'avarie,

## Interventions
date début, date fin, équipement, type de maintenance (préventive ou corrective), compte-rendu

## Site
type (soit "atelier de maintenance" pour la maintenance préventive, soit "centre de dépannage" pour la maintenance corrective), adresse, responsable

## Tâches
nom, intervention concernées

## Produits
nom, descriptif, unité de comptage, quantité réelle, seuil limite, gamme, catégorie, date du premier enregistrement

## Magasins
nom, adresse
