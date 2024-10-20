# Dictionnaire de données
Le __dictionnaire de données__ apporte des informations détaillées sur les champs des tables.

Il est question pour chaque champ de table, d'expliquer les éléments suivants: 

code, signification, type, longueur, nature, calcul (règle de calcul), Règle

## Cas de l'entité __interventions__

Rappel du MLD d'une intervention:

interventions (code_interventions, date_debut_interventions, date_fin_interventions, type_de_maintenance_interventions, compte_rendu_interventions, #code_moyen_roulant, #code_sites)

__Champ 1 : code_interventions__
- code: code_interventions
- signification: identifiant unique d'une intervention
- type: chaîne de caractères
- longueur: 8 caractères
- nature: E (pour élémentaire)
- Calcul (règle de calcul): aucun
- Règle: valeur générée par le système sur la base d'autres informations : moyen roulant, date, etc.

__Champ 2 : date_debut_interventions__
- code: date_debut_interventions
- signification: date de début prévue pour l'intervention
- type: date
- longueur: 10 caractères
- nature: E (pour élémentaire)
- Calcul (règle de calcul): aucun
- Règle: date fixée par le/la responsable de la maintenance

__Champ 3: date_fin_interventions__
- code: date_fin_interventions
- signification: date de fin prévue pour l'intervention
- type: date
- longueur: 10 caractères
- nature: E (pour élémentaire)
- Calcul (règle de calcul): aucun
- Règle: date non fixée à l'avance

__Champ 4: type_de_maintenance_interventions__
- code: type_de_maintenance_interventions
- signification: type de maintenance à réaliser : soit préventive, soit corrective
- type: chaîne de caractères
- longueur: 10 caractères
- nature: E (pour élémentaire)
- Calcul (règle de calcul): aucun
- Règle: la maintenance préventive est effectuée à des intervalles de temps connus et régulier, la maintenance corrective est réalisée à l'apparition d'une avarie sur le moyen roulant

__Champ 5: compte_rendu_interventions__
- code:  compte_rendu_interventions
- signification: sorte de reour d'expérience sur l'intervention effectuée
- type: chaîne de caractères
- longueur: 250 caractères
- nature: E (pour élémentaire)
- Calcul (règle de calcul): aucun
- Règle: faire un résumé du travail effectué : les points bloquants, les solutions mises en oeuvre

__Champ 6: #code_moyen_roulant__
- code: code_moyen_roulant
- signification: identifiant unique d'un moyen roulant
- type: chaîne de caractères
- longueur: 10 caractères
- nature: E (pour élémentaire)
- Calcul (règle de calcul): aucun
- Règle: clé primaire de la table "moyen roulant"

__Champ 7: #code_sites__
- code: code_sites
- signification: identifiant unique d'un site
- type: chaîne de caractères
- longueur: 10 caractères
- nature: E (pour élémentaire)
- Calcul (règle de calcul): aucun
- Règle: clé primaire de la table "site"
