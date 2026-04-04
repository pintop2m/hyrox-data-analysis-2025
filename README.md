# Hyrox Paris 2025 : Projet Data de A à Z sur la course Hyrox Paris 2025 : Web Scraping (BeautifulSoup), Data Processing (Pandas) et création d'un Dashboard interactif (Looker Studio).

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Pandas](https://img.shields.io/badge/Pandas-Data_Processing-150458.svg)
![Looker Studio](https://img.shields.io/badge/Looker_Studio-Dashboarding-4285F4.svg)

## Présentation du Projet
Ce projet est une analyse de bout en bout des performances des athlètes (catégories Doubles Open & Pro) lors de la course de fitness fonctionnel **Hyrox Paris 2025**. 
L'objectif était d'extraire des données web, de les nettoyer et de les modéliser pour créer un tableau de bord interactif permettant d'analyser la gestion de l'effort (pacing) et les stratégies de course.

🔗 **[https://lookerstudio.google.com/reporting/3f4dca34-77bb-4697-ad73-adb27ec8bef7]**

## Architecture et Méthodologie

### 1. Data Collection (Web Scraping)
Extraction des temps de course via un script Python personnalisé utilisant `requests` et `BeautifulSoup`.
* **Le Challenge Technique :** Le site officiel utilisant des requêtes asynchrones (AJAX) pour charger les temps détaillés par atelier (Splits), le script a été optimisé pour forcer l'interrogation de l'URL source cachée (via un paramètre `&pidp=details_splits`) afin d'aspirer les données brutes.

### 2. Data Processing & Feature (Pandas)
* Nettoyage des chaînes de caractères et gestion des doublons.
* Conversion de tous les chronos (formats textuels MM:SS) en format **Secondes (Int)** pour permettre l'agrégation mathématique sur Looker Studio.
* **Création de variables métiers :** * `Niveau_Elite` : Identification du Top 10 par catégorie.
  * `Objectif_Temps` : Segmentation des athlètes par tranches de temps final pour alimenter le "Race Planner".

### 3. Data Visualization (Looker Studio)
Création d'un rapport interactif de 5 pages incluant :
* **Vue d'Ensemble :** Vue globale et Leaderboard.
* **Analyse des Stations :** Temps moyen par station et corrélations.
* **Course à Pied & Transitions :** Analyse de la courbe de fatigue (8x1km Runs) et du temps passé en Roxzone.
* **?? :** Outil de recherche individuelle pour comparer un athlète à la moyenne de sa catégorie.
* **?? :** Modélisation prescriptive des allures cibles par tranche d'objectif de temps final.

## Aperçu du Tableau de Bord
*(Ajoute ici une image de ton dashboard : `![Dashboard Page 1](images/dashboard1.png)`)*

## Key Insights (Principales Découvertes)
* *Insight 1 : Le Top 10 Pro gagne principalement son avance sur la course à pied et les Wall Balls*
* *Insight 2 : L'allure de course s'effondre en moyenne de X% entre le Run 1 et le Run 8*
