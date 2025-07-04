# Projet ETL - Production Industrielle au Maroc (2005-2013)

## Contexte
Projet réalisé dans le cadre du module Business Intelligence (CI-ISBD/S8) à l'ENSA en mai 2025. L'objectif était de construire un entrepôt de données analysant la production industrielle marocaine entre 2005 et 2013, en intégrant des données industrielles et pluviométriques.

## Objectifs
- Modéliser un entrepôt de données avec schéma en étoile.
- Développer un processus ETL avec SSIS pour intégrer des sources Excel.
- Visualiser les indicateurs clés et explorer l'impact de la pluviométrie via Power BI.

---

## Architecture de l'Entrepôt
### Tables de Dimensions
- **`dim_temps`** : Années et données pluviométriques (situation "Normale/Pluvieuse").
- **`dim_branche`** : Secteurs industriels (Agro-alimentation, Textile, Chimie, etc.).
- **`dim_indicateur`** : Types d'indicateurs (Taux de croissance, Valeur ajoutée, etc.).

### Table de Faits
- **`fact_production`** : Mesures liées aux indicateurs, avec clés étrangères vers les dimensions.

>![image](https://github.com/user-attachments/assets/ead40115-ee16-407b-b5aa-9a75435610d4)

---

## Processus ETL (SSIS)
### Sources de Données
- **Fichiers Excel** : 
  - Statistiques industrielles (2006-2012).
  - Données pluviométriques (1991-2015).

### Étapes Clés
1. **Préparation des données** :
   - Transformation des années en lignes via `Unpivot`.
   - Nettoyage et ajout de colonnes (ex: "Indicateur").
2. **Chargement des dimensions** :
   - Utilisation de `Lookup` pour mapper les IDs.
3. **Alimentation des faits** :
   - Jointure des données industrielles et pluviométriques via `id_temps`.

>![image](https://github.com/user-attachments/assets/f89b17fc-41fa-46dd-ac34-d7c2ef782a42)


> *Data Flow Task : Staging_industrielles*
> ![image](https://github.com/user-attachments/assets/60bb4eb3-338f-4dd1-85c6-4b79b87a0cbf)
---

## Visualisation Power BI
### Tableaux de Bord
- **Évolution annuelle** par branche industrielle.
- **Comparaison des indicateurs** (ex: Taux d'investissement vs pluviométrie).
- **Prédictions** : Analyse de l'impact des conditions météorologiques sur la production.
- **Graphiques clés** :
  - Courbes temporelles.
  - Matrices comparatives (ex: Valeur moyenne par année et situation pluviométrique).

>![image](https://github.com/user-attachments/assets/dd446ff9-106e-4e1b-ae5b-12fe81739196)


### Exemple d'Insight
- Les années pluvieuses (ex: 2009-2011) corrèlent avec une hausse des investissements dans le secteur "Électricité et électronique".

---

## Auteur
- **Hafid GARHOUM** 

---

*Ce projet illustre la puissance des outils ETL et BI pour l'analyse de données sectorielles complexes.*
