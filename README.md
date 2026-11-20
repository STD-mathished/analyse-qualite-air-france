# Analyse et Prédiction de la Qualité de l'Air en France (IQA)

Projet d'analyse exploratoire de données, de validation statistique et de modélisation prédictive portant sur les relevés de 488 stations de surveillance atmosphérique en France entre 2018 et 2024.

---

## Contexte et objectifs
L'objectif de ce projet est de comprendre les facteurs qui influencent la qualité de l'air en milieu urbain, périurbain, rural et industriel, et de prédire l'**Indice de Qualité de l'Air (`indice_IQA`)** à partir des mesures de polluants et des conditions météorologiques :

1. **Nettoyage et préparation des données :** Suppression des doublons, standardisation des variables textuelles, filtrage des valeurs physiquement aberrantes et imputation statistique (moyenne ou médiane selon l'asymétrie des distributions).
2. **Analyse exploratoire (EDA) :** Étude univariée et multivariée des polluants ($PM_{2.5}$, $PM_{10}$, $NO_2$, $O_3$, $CO$, $SO_2$), comparaisons géographiques par ville et par zone, et suivi temporel.
3. **Tests d'hypothèses statistiques :** Validation par ANOVA et corrélation de Spearman (impact du trafic routier sur le $NO_2$, effet du vent sur la dispersion des particules fines, disparités selon le type de zone).
4. **Machine Learning :** Entraînement et comparaison de modèles de régression pour estimer l'IQA.

---

## Principaux résultats

* **Polluants les plus déterminants :** Les particules fines ($PM_{2.5}$) et le dioxyde d'azote ($NO_2$) présentent la plus forte corrélation positive avec la dégradation de l'IQA.
* **Tests statistiques :** Le lien entre la densité du trafic routier et la concentration en $NO_2$ est statistiquement significatif ($p < 0,001$).
* **Comparaison des modèles prédictifs (jeu de test) :**

| Modèle | MAE | RMSE | $R^2$ |
| :--- | :---: | :---: | :---: |
| **Régression Linéaire** | **15.19** | **20.27** | **0.80** |
| Arbre de Décision | 22.50 | 29.88 | 0.56 |

La **Régression Linéaire** explique environ 80 % de la variance de l'IQA et surpasse nettement l'Arbre de Décision, qui souffre de sur-apprentissage (*overfitting*) sur ce volume de données.

---

## Structure du dépôt

```text
analyse-qualite-air-france/
├── data/
│   └── dataset_qualite_air_brut.csv    # Jeu de données brut (488 relevés, 17 variables)
├── notebooks/
│   └── analyse_qualite_air.ipynb       # Carnet Jupyter complet (nettoyage, EDA, stats, ML)
├── exports/
│   └── exported_carnet.html
│   └── exported_carnet.pdf
└── README.md