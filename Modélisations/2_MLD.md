# MLD

agents (id_Agent, matricule_Agent, nom_Agent, prenom_Agent, poste_Agent, departement_Agent, date_naissance_Agent, téléphone_Agent)

produits (id_produits, code_produits, nom_produits, description_produits, type_produits, gamme_produits, categorie_produits, unite_de_comptage_produits, qtite_reelle_produits, seuil_alerte_produits, date_premier_enregistrement_produits, alerte_produit_produits, #code_magasins) 

magasins (code_magasins, nom_magasins, adresse_magasins, #code_sites) 

interventions (code_interventions, date_debut_interventions, date_fin_interventions, type_de_maintenance_interventions, compte_rendu_interventions, #code_moyen_roulant) 

sites (code_sites, nom_sites, type_sites, adresse_sites, coordonnees_gps_sites, telephone_sites, responsable_sites) 

moyens_roulant (code_moyen_roulant, conduite_moyen_roulant, arrivee_moyen_roul, mise_en_service_moyen_roul, depart_moyen_roul, pmp_moyen_roul, #nom_usage) 

equipements (code_equipements, nom_equipements, #code_moyen_roulant) 

usage (nom_usage) 

statuts (nom_statuts) 

taches (code_Entite_10, nom_Entite_10) 

produits_inseres (id_Agent, id_produits, date_insertion_inserer, quantite_inseree_inserer) 

exploitation (id_Agent, code_moyen_roulant, date_exploitation_exploitation) 

produits_utilises (id_produits, code_interventions, date_utilisation_utiliser, quantite_utilisee_utiliser) 

bon_de_missions (id_Agent, code_interventions, date_affectation_bon_de_missions) 

taches_effectuees (code_interventions, code_Entite_10) 

concerner (code_interventions, code_equipements, date_equipement_intervention_concerner) 

historique_statuts (code_moyen_roulant, nom_statuts, date_historique_statuts)
