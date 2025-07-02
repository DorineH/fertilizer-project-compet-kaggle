### Contexte du projet
Nous avons participé à la compétition Kaggle “Playground Series S5E6” dont l’objectif était de prédire, pour chaque parcelle, les trois engrais les plus adaptés selon les conditions de culture, de sol et de météo. La performance était d'évaluée via la métrique MAP@3.

### Équipe
Ce projet a été mené par Lisa AU et Dorine HENRY, étudiante en Master Stratégie digital option tech lead dev.

### Environnement et langage
Nous avons choisi le langage Python pour sont large écosystème. Les bibliothèques spécialisées tèl que que : pandas, scikit-lear, LightGBM/CatBoost, matplotlib/seaborn, nous on permis d'explorer et de manipuler les données, decter les anomalies, de comparer différent algorithmes, d'exploiter des modèles et de visualiser les corrélations.

### Algorithme testé et utilisé
Nous avons évalué plusieurs familles de modèles pour maximiser notre MAP@3 :
- Régression logistique multiclass (scikit-learn).
- Forêt aléatoire (RandomForestClassifier).
- Gradient boosting via XGBoost et CatBoost.
- LightGBM (lightgbm.LGBMClassifier).

Nous avons retenu LightGBM car nous avons obtenue les meilleur perofmance, une meilleur rapidité d'entraînement, simplicité d'intégration dans la pipline.

### Approche générale
Notre pipeline s’articule en cinq grandes étapes :

Exploration des données (EDA) – prise en main rapide du dataset via shape, info(), describe(), visualisations de distributions et matrices de corrélation. Grâce à matplotlib.pyplot et seaborn.
Pré-traitement – encodage des variables catégorielles (LabelEncoder pour les cibles et les colonnes de type sol et culture), suppression des colonnes non-utiles (identifiants, noms), et gestion des valeurs manquantes.
Feature engineering – création d’agrégats météo (moyenne et nombre de jours chauds sur 7 jours) et de variables d’interaction entre le type de sol et la culture.
Modélisation et validation – mise en place d’une validation croisée stratifiée (StratifiedKFold à 5 plis) avec calcul d’un score MAP@3 custom à chaque itération.
Soumission – agrégation des prédictions out-of-fold, extraction du top-3 et génération du fichier submission.csv, puis envoi via l’API Kaggle.

### Optimisation du code
Pour accélérer l’entraînement et réduire la consommation de la mémoire, nous avons :

Inséré des appels à gc.collect() après chaque pli de validation.
Structuré la boucle de cross-validation de façon à agréger les prédictions et les probabilités.
Encapsulé le pré-traitement et le modèle dans un Pipeline scikit-learn (imputeur → encodeur → estimateur).

### Modèle final
Le modèle retenu est un classifieur LightGBM multiclass avec early stopping (50 tours sans amélioration) et log_evaluation. Les hyperparamètres clés ajustés sont learning_rate, num_leaves et max_depth. Cette configuration nous a permis d’atteindre un score OOF MAP@3 de 0.33405.

### Problèmes rencontrés
Nous avons rancontré quelque difficulté lié à notre performance de nos pc.
Les limites de mémoire d’exécution imposées par l’environnement Kaggle.


