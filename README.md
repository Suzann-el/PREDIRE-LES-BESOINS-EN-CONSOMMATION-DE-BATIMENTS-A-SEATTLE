# ⚡ Seattle Building Energy — Prédiction de consommation & émissions GES

Modélisation de la consommation énergétique et des émissions de gaz à effet de serre
de **3 376 bâtiments commerciaux et résidentiels** de Seattle,
à partir des données open data du programme [Seattle Building Energy Benchmarking](https://data.seattle.gov/).

---

## Contexte & enjeux

Les bâtiments représentent une part majeure de la consommation énergétique urbaine.
Ce projet modélise deux grandeurs physiques clés :

- **`SiteEnergyUse (kBtu)`** — énergie totale consommée sur site (électricité + gaz naturel + vapeur)
- **`TotalGHGEmissions (tCO₂e)`** — émissions de gaz à effet de serre associées

L'objectif est de prédire ces deux cibles à partir des caractéristiques structurelles,
géographiques et d'usage des bâtiments — sans compteur temps réel.

---

## Données

| Caractéristique | Valeur |
|---|---|
| Source | Seattle Open Data Portal (Kaggle) |
| Années | 2015 – 2016 |
| Bâtiments | 3 376 |
| Features initiales | 46 |
| Cibles | `SiteEnergyUse(kBtu)` · `TotalGHGEmissions` |

**Types de bâtiments couverts** : hôtels, bureaux, commerces, résidences, hôpitaux, entrepôts, campus universitaires…

---

## Feature engineering

Les variables brutes ont été enrichies avec des features physiques et structurelles :

| Feature construite | Interprétation |
|---|---|
| `BuildingAge` | Ancienneté du bâtiment (proxy d'isolation thermique) |
| `haversine_distance` | Distance au centre-ville de Seattle (géospatial) |
| `RateParking` | Part de la surface dédiée au parking |
| `RatePerFloors` | Surface moyenne par étage |
| `RateLargestPropertyUseType` | Concentration d'usage principal |
| `SiteEnergyUse_Log` · `TotalGHGEmissions_Log` | Transformation log pour normaliser les distributions |

Les trois flux énergétiques — **électricité**, **gaz naturel** et **vapeur** — sont traités
comme un système multi-sources dont l'interaction détermine la consommation globale.

---

## Modélisation

Deux notebooks de prédiction, un par cible :

### Modèles testés

| Modèle | Type |
|---|---|
| `DummyRegressor` | Baseline |
| `Ridge` / `Lasso` | Régression linéaire régularisée |
| `SVR` / `LinearSVR` | Support Vector Regression |
| `RandomForestRegressor` | Ensemble — bagging |
| `LightGBM` | Ensemble — gradient boosting |

### Métriques d'évaluation

`MAE` · `RMSE` · `MAPE` · `R²` — évaluées en cross-validation 5 folds.

---

## Structure du projet

```
seattle-building-energy/
│
├── notebooks/
│   ├── 1_exploration.ipynb          # EDA, nettoyage, feature engineering
│   ├── 2_prediction_energy.ipynb    # Modélisation SiteEnergyUse
│   └── 3_prediction_ghg.ipynb      # Modélisation TotalGHGEmissions
│
├── data/
│   └── building_energy_propre.csv   # Dataset nettoyé
│
└── README.md
```

---

## Stack technique

`Python 3.9` · `pandas` · `scikit-learn` · `LightGBM` · `Plotly` · `Seaborn` · `haversine`

---

## Résultats clés

> Les modèles ensemblistes (Random Forest, LightGBM) surpassent significativement
> la baseline sur les deux cibles, avec des R² supérieurs à 0.85 sur le jeu de test.
> Le `BuildingAge` et la surface par étage (`RatePerFloors`) ressortent comme
> les features les plus prédictives de la consommation énergétique.

---

## Auteure

**Saoussan EL HAOUZI** — Data Scientist
[GitHub](https://github.com/Suzann-el)
