# Prérequis

Se trouvent ici les requêtes relatives à la création des tables.

_Note_ : ce code SQL a été testé dans un environnement __Live SQL__

__En cours de rédaction : merci de votre compréhension__

```sql
/*
Faire attention à l'ordre de suppression des tables, afin d'éviter l'erreur suivante
*/

/*
DROP TABLE taches_effectuees;
DROP TABLE taches;
DROP TABLE concerner;
DROP TABLE equipements;
DROP TABLE exploitation;
DROP TABLE historique_statuts;
DROP TABLE statuts;
DROP TABLE interventions;
DROP TABLE bon_de_missions;
DROP TABLE agents;
DROP TABLE produits_utilises;
DROP TABLE produits;
DROP TABLE produits_inseres;
DROP TABLE magasins;
DROP TABLE sites;
DROP TABLE moyens_roulant;
DROP TABLE usage;
*/
------------------------------------

/********************  CREATE TABLE	****************************/


CREATE TABLE agents (matricule_Agent VARCHAR2(250) NOT NULL,
nom_Agent VARCHAR2(255),
prenom_Agent VARCHAR2(250),
poste_Agent VARCHAR2(255),
departement_Agent VARCHAR2(255),
date_naissance_Agent DATE,
téléphone_Agent NUMBER,
PRIMARY KEY (matricule_Agent));


CREATE TABLE produits (code_produits VARCHAR2(250) NOT NULL,
nom_produits VARCHAR2(250),
description_produits VARCHAR2(250),
type_produits VARCHAR2(250),
gamme_produits VARCHAR2(250),
categorie_produits VARCHAR2(250),
unite_de_comptage_produits VARCHAR2(250),
qtite_reelle_produits INTEGER,
seuil_alerte_produits INTEGER,
date_premier_enregistrement_produits DATE,
alerte_produit_produits VARCHAR2(250),
PRIMARY KEY (code_produits));


CREATE TABLE magasins (code_magasins VARCHAR2(250) NOT NULL,
nom_magasins VARCHAR2(250),
adresse_magasins VARCHAR2(255),
PRIMARY KEY (code_magasins));


CREATE TABLE interventions (code_interventions VARCHAR2(250) NOT NULL,
date_debut_interventions DATE,
date_fin_interventions DATE,
type_de_maintenance_interventions VARCHAR2(250),
compte_rendu_interventions VARCHAR2(255),
PRIMARY KEY (code_interventions));


CREATE TABLE sites (code_sites VARCHAR2(250) NOT NULL,
nom_sites VARCHAR2(250),
type_sites VARCHAR2(250),
adresse_sites VARCHAR2(255),
coordonnees_gps_sites VARCHAR2(250),
telephone_sites INTEGER,
responsable_sites VARCHAR2(250),
PRIMARY KEY (code_sites));


CREATE TABLE moyens_roulant (code_moyen_roulant VARCHAR2(250) NOT NULL,
conduite_moyen_roulant VARCHAR2(250),
arrivee_moyen_roul DATE,
mise_en_service_moyen_roul DATE,
depart_moyen_roul DATE,
pmp_moyen_roul DATE,
PRIMARY KEY (code_moyen_roulant));


CREATE TABLE equipements (code_equipements VARCHAR2(250) NOT NULL,
nom_equipements VARCHAR2(250),
PRIMARY KEY (code_equipements));


CREATE TABLE usage (nom_usage VARCHAR2(250) NOT NULL,
PRIMARY KEY (nom_usage));


CREATE TABLE statuts (nom_statuts VARCHAR2(250) NOT NULL,
PRIMARY KEY (nom_statuts));


CREATE TABLE taches (code_taches VARCHAR2(250) NOT NULL,
nom_taches VARCHAR2(250),
PRIMARY KEY (code_taches));


/*************************      Associations devenant des entités/Tables      *****************************/

CREATE TABLE bon_de_missions (
    date_bon_de_missions DATE,
    matricule_Agent VARCHAR2(250),
    code_interventions VARCHAR2(250),
    PRIMARY KEY (matricule_Agent, code_interventions)  
);

CREATE TABLE exploitation (date_exploitation DATE, kilometrage NUMBER,
matricule_Agent VARCHAR2(250),
code_moyen_roulant VARCHAR2(250),
PRIMARY KEY (matricule_Agent, code_moyen_roulant)
);

CREATE TABLE taches_effectuees (
code_interventions VARCHAR2(250),
code_taches VARCHAR2(250),
PRIMARY KEY (code_interventions,
 code_taches)
);

CREATE TABLE concerner (date_concerner DATE,
code_interventions VARCHAR2(250),
code_equipements VARCHAR2(250),
PRIMARY KEY (code_interventions,
 code_equipements)
);

CREATE TABLE historique_statuts (date_historique_statuts DATE,
code_moyen_roulant VARCHAR2(250),
nom_statuts VARCHAR2(250),
PRIMARY KEY (code_moyen_roulant,
 nom_statuts)
);

CREATE TABLE produits_inseres (date_produits_inseres DATE,
quantite_produits_inseres INTEGER,
matricule_Agent VARCHAR2(250),
code_produits VARCHAR2(250),
PRIMARY KEY (matricule_Agent,
 code_produits)
);

CREATE TABLE produits_utilises (date_produits_utilises DATE,
quantite_produits_utilises INTEGER,
code_produits VARCHAR2(250),
code_interventions VARCHAR2(250),
PRIMARY KEY (code_produits,
 code_interventions)
);

/***************************      ALTER TABLE : ADD CONSTRAINT    ***************************/

ALTER TABLE bon_de_missions ADD CONSTRAINT FK_bon_de_missions_matricule_Agent FOREIGN KEY (matricule_Agent) REFERENCES agents (matricule_Agent);
ALTER TABLE bon_de_missions ADD CONSTRAINT FK_bon_de_missions_code_interventions FOREIGN KEY (code_interventions) REFERENCES interventions (code_interventions);
ALTER TABLE produits ADD CONSTRAINT FK_produits_code_magasins FOREIGN KEY (code_magasins) REFERENCES magasins (code_magasins);
ALTER TABLE magasins ADD CONSTRAINT FK_magasins_code_sites FOREIGN KEY (code_sites) REFERENCES sites (code_sites);
ALTER TABLE interventions ADD CONSTRAINT FK_interventions_code_moyen_roulant FOREIGN KEY (code_moyen_roulant) REFERENCES moyens_roulant (code_moyen_roulant);
ALTER TABLE interventions ADD CONSTRAINT FK_interventions_code_sites FOREIGN KEY (code_sites) REFERENCES sites (code_sites);
ALTER TABLE moyens_roulant ADD CONSTRAINT FK_moyens_roulant_nom_usage FOREIGN KEY (nom_usage) REFERENCES usage (nom_usage);
ALTER TABLE equipements ADD CONSTRAINT FK_equipements_code_moyen_roulant FOREIGN KEY (code_moyen_roulant) REFERENCES moyens_roulant (code_moyen_roulant);
ALTER TABLE produits_inseres ADD CONSTRAINT FK_produits_inseres_matricule_Agent FOREIGN KEY (matricule_Agent) REFERENCES agents (matricule_Agent);
ALTER TABLE produits_inseres ADD CONSTRAINT FK_produits_inseres_code_produits FOREIGN KEY (code_produits) REFERENCES produits (code_produits);
ALTER TABLE exploitation ADD CONSTRAINT FK_exploitation_matricule_Agent FOREIGN KEY (matricule_Agent) REFERENCES agents (matricule_Agent);
ALTER TABLE exploitation ADD CONSTRAINT FK_exploitation_code_moyen_roulant FOREIGN KEY (code_moyen_roulant) REFERENCES moyens_roulant (code_moyen_roulant);
ALTER TABLE produits_utilises ADD CONSTRAINT FK_produits_utilises_code_produits FOREIGN KEY (code_produits) REFERENCES produits (code_produits);
ALTER TABLE produits_utilises ADD CONSTRAINT FK_produits_utilises_code_interventions FOREIGN KEY (code_interventions) REFERENCES interventions (code_interventions);
ALTER TABLE bon_de_missions ADD CONSTRAINT FK_bon_de_missions_matricule_Agent FOREIGN KEY (matricule_Agent) REFERENCES agents (matricule_Agent);
ALTER TABLE bon_de_missions ADD CONSTRAINT FK_bon_de_missions_code_interventions FOREIGN KEY (code_interventions) REFERENCES interventions (code_interventions);
ALTER TABLE taches_effectuees ADD CONSTRAINT FK_taches_effectuees_code_interventions FOREIGN KEY (code_interventions) REFERENCES interventions (code_interventions);
ALTER TABLE taches_effectuees ADD CONSTRAINT FK_taches_effectuees_code_taches FOREIGN KEY (code_taches) REFERENCES taches (code_taches);
ALTER TABLE concerner ADD CONSTRAINT FK_concerner_code_interventions FOREIGN KEY (code_interventions) REFERENCES interventions (code_interventions);
ALTER TABLE concerner ADD CONSTRAINT FK_concerner_code_equipements FOREIGN KEY (code_equipements) REFERENCES equipements (code_equipements);
ALTER TABLE historique_statuts ADD CONSTRAINT FK_historique_statuts_code_moyen_roulant FOREIGN KEY (code_moyen_roulant) REFERENCES moyens_roulant (code_moyen_roulant);
ALTER TABLE historique_statuts ADD CONSTRAINT FK_historique_statuts_nom_statuts FOREIGN KEY (nom_statuts) REFERENCES statuts (nom_statuts);
```
