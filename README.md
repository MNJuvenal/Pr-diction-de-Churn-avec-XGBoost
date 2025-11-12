# 📉 Projet 1 : Prédiction du Churn Client avec XGBoost

## 🎯 Objectif du Projet

L'objectif principal de ce projet est de développer un modèle de Machine Learning performant, basé sur l'algorithme **XGBoost**, afin d'identifier les clients d'une entreprise de télécommunications qui présentent un risque élevé de désabonnement (Churn).

Le but est de fournir à l'équipe marketing ou de rétention une liste de clients à risque pour des actions ciblées, minimisant ainsi le taux de déperdition et les coûts associés.

## ⚙️ Méthodologie et Modélisation

### 1. Préparation des Données
* **Source de Données :** Jeu de données Telecom Churn .
* **Nettoyage :** Gestion des valeurs manquantes, notamment dans la colonne `TotalCharges`, et correction des types.
* **Ingénierie des Caractéristiques :** Encodage des variables catégorielles. Utilisation du **One-Hot Encoding** pour les variables nominales et du **Label Encoding** pour les variables binaires et la variable cible (`Churn`).
* **Séparation :** Division des données en ensembles d'entraînement et de test (**80%/20%**), avec stratification pour garantir une répartition égale de la classe `Churn`.

### 2. Modélisation et Optimisation
* **Algorithme :** **XGBoost Classifier** a été choisi pour sa performance sur les données tabulaires.
* **Optimisation :** Utilisation de **GridSearchCV** avec 5-fold Cross-Validation pour optimiser les hyperparamètres (ex: `max_depth`, `learning_rate`, `n_estimators`).
* **Métriques Cible :** Optimisation prioritaire sur le score **AUC-ROC**, plus fiable que l'Accuracy en cas de déséquilibre de classe.

## 📊 Résultats et Performance

Le modèle optimisé a été évalué sur l'ensemble de test (jamais vu).

### Score AUC-ROC Final
| Score |
| :---: |
| **0.8446** |

### Rapport de Classification (Classe Positive : Churn)

| Métrique | Churn (1) | Interprétation Clé |
| :---: | :---: | :--- |
| **Précision** | **0.66** | 66% des clients prédits comme 'Churn' l'étaient réellement. (Bon pour ne pas gaspiller d'offres). |
| **Rappel (Recall)** | **0.52** | 52% des clients qui allaient réellement 'Churn' ont été détectés. (Marge d'amélioration pour ne pas manquer de clients). |




## 💡 Interprétation des Résultats (Feature Importance)

L'analyse des variables les plus importantes pour la prédiction guide les actions de rétention :



Les facteurs les plus critiques de *Churn* sont :
1.  **InternetService\_fiber optic :** Les clients utilisant la fibre optique sont le groupe le plus à risque.
2.  **Contract\_One year / Two year :** Les contrats de longue durée réduisent significativement le risque de *Churn*.
3.  **PaymentMethod\_Electronic check :** Ce mode de paiement est fortement associé à un risque de *Churn* plus élevé.

---

## 💻 Instructions pour Exécuter le Projet

Ce projet est conçu pour être exécuté dans un environnement Python avec les dépendances listées ci-dessous.

### Dépendances

Installer les bibliothèques requises :

```bash
pip install pandas numpy scikit-learn xgboost matplotlib seaborn openpyxl
