# 🌿 Seattle — Prédiction des émissions carbone des bâtiments

> Modèles de régression supervisée pour prédire la consommation énergétique et les émissions CO₂ des bâtiments non résidentiels de Seattle.

---

## 🎯 Contexte

Dans le cadre de l'objectif **neutralité carbone 2050** de la ville de Seattle, ce projet vise à anticiper les émissions des bâtiments tertiaires sans avoir recours à des relevés coûteux sur site. Un bon modèle prédictif permet de cibler en priorité les bâtiments les plus énergivores pour les actions de rénovation.

---

## ⚙️ Ce que fait le projet

- **Analyse exploratoire** — distribution des consommations, corrélations, détection d'outliers
- **Feature engineering** — sélection et transformation des variables pertinentes (surface, année de construction, type de bâtiment...)
- **Modélisation supervisée** — comparaison de plusieurs modèles de régression
- **Évaluation** — comparaison des performances via RMSE, MAE, R²

---

## 🔍 Modèles comparés

| Modèle | Type |
|--------|------|
| Régression linéaire | Baseline |
| Random Forest | Ensemble |
| Gradient Boosting (XGBoost) | Ensemble boosté |
| Ridge / Lasso | Régularisation |

---

## 🛠️ Stack

`Python` `Scikit-learn` `XGBoost` `Pandas` `Matplotlib` `Seaborn`

---

## 📁 Structure du projet

```
├── notebooks/
│   ├── 01_exploration.ipynb       # Analyse exploratoire
│   └── 02_modelisation.ipynb      # Modèles et évaluation
└── README.md
```

---

## 📂 Données

Dataset public de la ville de Seattle — [2016 Building Energy Benchmarking](https://data.seattle.gov/dataset/2016-Building-Energy-Benchmarking/2bpz-gwpy)

Relevés de consommation énergétique et d'émissions GES pour les bâtiments non résidentiels de plus de 20 000 sq ft.
