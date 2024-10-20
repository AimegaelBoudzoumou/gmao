# Entités et Attributs

L'analyse du cahier des charges et des spécifications fonctionnelles permet de répérer les éléments (entités) amenés à interagir au sein d'un applicatif.
Chaque entité contient des attributs. Les entités sont reliées entre elles par des associations.

Plus tard, chaque entité sera représentée par une table dans la base de données; et les attributs seront les champs de ces tables.

<!--Ce tutoriel de IBM contient des informations détaillées sur le modèle relationnel: 
[data-modeling](https://www.ibm.com/fr-fr/topics/data-modeling)-->

## MR (pour Moyen Roulant)
code (concaténation de plusieurs informations), matériel (exemples: MP 89 CC, TMVI), conduite (conduite conducteur cc ou conduite automatique ca), statut (en service, en livraison, reformé, indisponible, sans affectation; et fait l'objet d'une table à part), usage (travaux, voyageurs; fait l'objet d'une table à part), arrivée, mise en service, départ, PMP (Prochaine Maintenance Préventive)

## Matériel
code, constructeur, composition, écartement des roues, longueur, intercirculation, vitesse maximale, affectation actuelle, livraison, période de service

## Ligne
numéro

## Equipement
code, nom, MR associé

## Agent/Employé
matricule, nom, prenom, poste, département (MRF ou Expoitation; peut faire l'objet d'une entité à part), date de naissance, téléphone

## Exploitation
agent exploitant, date, heure début, heure fin, kilométrage, avaries, compte-rendu de l'agent exploitant, lieu où la l'avariee est constatée, niveau de gravité de l'avarie

## Interventions
code, date début, date fin, type de maintenance (peut être une entité à part) préventive ou corrective, compte-rendu, équipement (se trouve en pratique dans une autre table)

## Site
code, nom, type (soit "atelier de maintenance" pour la maintenance préventive, soit "centre de dépannage" pour la maintenance corrective), adresse, coordonnées gps, telephone, responsable

## Tâches
code, nom, intervention concernées

## Produits
code, nom, descriptif, type, gamme, catégorie, unité de comptage, quantité réelle, seuil alerte, date du premier enregistrement, alerte_produit

## Magasins
code, nom, adresse
