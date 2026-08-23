# 🏒 Finnish Liiga — Match Outcome Prediction & Expected Goals (xG) Analytics (2025)

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit_learn-ML_Modeling-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-Ensemble-red?style=for-the-badge)
![Pandas](https://img.shields.io/badge/Pandas-Data_Analysis-150458?style=for-the-badge&logo=pandas&logoColor=white)

## 📌 Project Overview
An end-to-end Machine Learning and Sports Analytics project evaluating team performance metrics, shot quality ($xG$), and match outcomes across the **Finnish Liiga 2025 season**. 

The project follows the **PACE Framework** (Plan, Analyze, Construct, Execute) across 5 modular stages to classify match outcomes (`home_win` vs. `non-home win`) and identify the primary statistical drivers of victory in professional ice hockey.

---

## 📊 Data Source

The dataset contains official regular-season game data from the **Finnish Liiga** (2025 season), extracted via the official Liiga API:

🔗 **Official League Data:** [Liiga.fi](https://liiga.fi)

The dataset covers regular-season match records, final scores, period breakdowns, attendance figures, and Expected Goals ($xG$) calculated from shot location and event metrics.

---

## 📂 Repository Structure
```text
├── README.md
├── data/
│   └── liiga_games_2025.csv                          # Extracted feature subset from Liiga API (selected match, goal, xG, and attendance columns)
├── images/                                           # Visualizations, EDA charts & feature importances
│   ├── confusion_matrix_logistic_regression.png
│   ├── correlation_heatmap_liiga_dataset.png
│   ├── feature_importances_random_forest.png
│   ├── home_goals_boxplot.png
│   ├── home_goals_histogram.png
│   ├── liiga_outcomes_pie_chart.png
│   └── liiga_xg_vs_goals_scatter.png
├── models/
│   └── liiga_champion_model.pickle                   # Serialized XGBoost champion model
├── notebooks/                                        # 5 PACE Project Stages
│   ├── 01_liiga_data_exploration.ipynb               # Data extraction, schema verification & cleaning
│   ├── 02_liiga_exploratory_data_analysis.ipynb      # EDA, distributions & correlation analysis
│   ├── 03_liiga_hypothesis_testing.ipynb             # Two-sample t-tests & statistical validation
│   ├── 04_logistic_regression.ipynb                  # Baseline classification & odds ratio analysis
│   └── 05_machine_learning_liiga.ipynb               # Random Forest & XGBoost tuning (GridSearchCV)
└── presentations/                                    # Executive Summary slide decks
    ├── 01_executive_summary.pptx
    ├── 02_executive_summary.pptx
    ├── 03_executive_summary.pptx
    ├── 04_executive_summary.pptx
    └── 05_executive_summary.pptx

---

## 💡 Key Metrics & Analytical Insights

**General Season Summary (2025 Season):**
- **Target Variable:** Binary match outcome (`home_win` vs. non-home win).
- **Primary Signal Driver:** Expected goals metrics (`home_xg_share`, `home_xg`, `away_xg`, and `xg_diff`) are the most influential features in the tree-based models.
- **Shot Quality Focus:** Shot danger value (xG) is the key predictor of scoring efficiency compared to raw match attendance.

**Machine Learning Model Comparison (Validation Set):**
- **Champion Model:** **XGBoost Classifier** (selected over Random Forest).
- **Home Win Recall:** **76.0%** — correctly identified 48 out of 63 actual home victories on the validation set.
- **Validation Accuracy:** **54.0%** (vs. 52.0% for Random Forest).
- **Home Win F1-Score:** **0.64** (vs. 0.60 for Random Forest).
- **Model Persistence:** Serialized via `pickle` for pipeline reproducibility.

---

## 🛠️ Data Pipeline & Technical Architecture

- **Data Ingestion & Cleaning:** Extracted structured game records via requests/API, handled missing values, and created derived metrics (`xg_diff`, `home_xg_share`, `total_xg`).
- **Exploratory Data Analysis & Statistical Testing:** Conducted two-sample t-tests to evaluate the statistical significance of home vs. away goal generation and attendance impact.
- **Machine Learning Architecture:** Implemented a stratified 60% Train / 20% Validation / 20% Holdout Test split. Tuned Hyperparameters for Logistic Regression, Random Forest, and XGBoost classifiers.
- **Evaluation & Explainability:** Evaluated model performance using classification reports (precision, recall, f1-score, accuracy), confusion matrices, and feature importance bar plots (`feature_importances_`).

---

## 💡 Next Steps & Strategic Takeaways

- **Tactical Scheme:** Focus coaching schemes on slot entries and passes into high-danger areas rather than low-probability perimeter shots.
- **Home Momentum:** Establish aggressive forechecking in the 1st period to secure early xG dominance on home ice.
- **Pre-Game Feature Engineering:** Integrate 5-game rolling historical xG averages and fatigue metrics (days of rest, travel distance) for pre-match forecasting.

---

## 👩‍💻 Author

**Oksana Kocherzhat**  
Data Analyst (OAMK)  
📍 Finland  
🔗 LinkedIn: [linkedin.com/in/oksana-kocherzhat-834518231](https://www.linkedin.com/in/oksana-kocherzhat-834518231)
