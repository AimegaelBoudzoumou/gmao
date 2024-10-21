# MLD

## Principe de fonctionnement du MLD

Le MLD (pour modèle logique de données) est une couche intermédiaire entre le MCD et la base de données.

- Les entités et attributs dans le MCD deviennent respectivement des tables et des champs.

- Les associations ayant la cardinalité max N,N se transforment en tables.

 - Lorsqu'une association reliant deux éléments A et B, possède la cardinalité max 1,N (soit 1 pour A et N pour B) : 

l'élément A reçoit la clé primaire de l'élément B. Cette clé primaire se transforme en clé étrangère dans A.


### Voici les tables et leurs champs, découlant du MCD:

__agents__ (matricule_Agent, nom_Agent, prenom_Agent, poste_Agent, departement_Agent, date_naissance_Agent, téléphone_Agent) 

__produits__ (code_produits, nom_produits, description_produits, type_produits, gamme_produits, categorie_produits, unite_de_comptage_produits, qtite_reelle_produits, seuil_alerte_produits, date_premier_enregistrement_produits, alerte_produit_produits, #code_magasins) 

__magasins__ (code_magasins, nom_magasins, adresse_magasins, #code_sites) 

__interventions__ (code_interventions, date_debut_interventions, date_fin_interventions, type_de_maintenance_interventions, compte_rendu_interventions, #code_moyen_roulant, #code_sites) 

__sites__ (code_sites, nom_sites, type_sites, adresse_sites, coordonnees_gps_sites, telephone_sites, responsable_sites) 

__moyens_roulant__ (code_moyen_roulant, conduite_moyen_roulant, arrivee_moyen_roul, mise_en_service_moyen_roul, depart_moyen_roul, pmp_moyen_roul, #nom_usage) 

__equipements__ (code_equipements, nom_equipements, #code_moyen_roulant) 

__usage__ (nom_usage) 

__statuts__ (nom_statuts) 

__taches__ (code_taches, nom_taches) 

__produits_inseres__ (matricule_Agent, code_produits, date_produits_inseres, quantite_produits_inseres) 

__exploitation__ (matricule_Agent, code_moyen_roulant, date_exploitation) 

__produits_utilises__ (code_produits, code_interventions, date_produits_utilises, quantite_produits_utilises) 

__bon_de_missions__ (matricule_Agent, code_interventions, date_bon_de_missions) 

__taches_effectuees__ (code_interventions, code_taches) 

__concerner__ (code_interventions, code_equipements, date_concerner) 

__historique_statuts__ (code_moyen_roulant, nom_statuts, date_historique_statuts)

### Recherche à faire : soulignement de la clé primaire dans le MLD via analyseSI
