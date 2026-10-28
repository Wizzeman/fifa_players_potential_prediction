# FIFA Player Potential Prediction ⚽

A machine learning project that predicts FIFA player potential ratings using player attributes, performance statistics, and player-specific characteristics. The project explores data preprocessing, exploratory data analysis, feature engineering, and regression modeling to estimate player potential and identify promising young players.

## 📌 Project Overview

Player potential is an important indicator of how much a football player can develop over time. However, predicting potential using only a player's current overall rating may not fully capture the differences between positions and individual player attributes.

This project aims to build machine learning models that predict player potential based on relevant features from a FIFA player dataset.

To account for differences between playing positions, the project explores **position-specific regression models** for four main player roles:

- **Forwards:** ST, CFو LW, RW
- **Midfielders:** CM, CDM, CAMو LM, RM
- **Defenders:** CB, RB, RWB, LB, LWB
  
The goal is to investigate whether specialized models can better capture the characteristics of players in different positions.

## 🎯 Objectives

- Perform exploratory data analysis (EDA) to understand player characteristics and feature distributions.
- Clean and preprocess the dataset.
- Analyze relationships between player attributes and potential ratings.
- Engineer meaningful features to improve predictive performance.
- Investigate feature selection and the importance of different player attributes.
- Build and evaluate regression models.
- Compare model performance across different player positions.
- Identify promising young players based on their predicted potential.

## 📂 Dataset

The dataset contains FIFA player information, including demographic characteristics, player ratings, financial information, and technical attributes.

### Main features

| Category | Examples |
|---|---|
| Player information | Name, age, nationality, height, weight |
| Ratings | Overall rating, potential |
| Financial information | Market value, wage, release clause |
| Player characteristics | Preferred foot, weak foot, skill moves |
| Attacking attributes | Finishing, dribbling, positioning |
| Passing attributes | Short passing, long passing, vision, crossing |
| Physical attributes | Acceleration, sprint speed, stamina, strength |
| Defensive attributes | Interceptions, marking, standing tackle, sliding tackle |
| Goalkeeping | Position-specific features, where available |

**Target variable:** `potential`

The `overall_rating` feature can be investigated as a predictor, but its inclusion should be evaluated carefully to understand how much predictive information it contributes.

> **Dataset note:** The dataset is not necessarily included in this repository. Check the original dataset's source and licensing terms before redistributing it. Place your local dataset in the expected data directory or update the notebook paths accordingly.

## 🛠️ Technologies Used

- **Python** — Core programming language
- **Pandas** — Data manipulation and analysis
- **NumPy** — Numerical computations
- **Matplotlib** — Data visualization
- **Seaborn** — Statistical visualization
- **Scikit-learn** — Preprocessing, regression, and model evaluation
- **Jupyter Notebook** — Interactive analysis and experimentation
- **Git & GitHub** — Version control

## 🔍 Project Workflow

### 1. Data Understanding and Cleaning

The initial stage focuses on understanding the structure and quality of the dataset.

Tasks include:

- Inspecting dataset dimensions and column data types.
- Data Understanding and Cleaning
- Checking inconsistent or invalid values.
- Analyzing numerical and categorical features.
- Preparing the data for exploratory analysis and modeling.

### 2. Exploratory Data Analysis (EDA)

EDA is used to understand player characteristics and discover patterns in the dataset.

Areas of investigation include:

- Distributions of age, overall rating, potential, market value, and wages.
- Relationships between overall rating and potential.
- Correlations between player attributes.
- Differences in attributes across player positions.
- Outliers and skewness in numerical features.
- Characteristics of younger players with high potential.

### 3. Feature Selection

Feature selection is performed separately for forwards, midfielders, and defenders. Each group uses a different set of player attributes based on the characteristics of its playing role.

Examples of selected features include:

- **Forwards:** Finishing, dribbling, ball control, shot power, positioning, and sprint speed.
- **Midfielders:** Short passing, long passing, vision, dribbling, interceptions, and ball control.
- **Defenders:** Interceptions, standing tackle, sliding tackle, marking, heading accuracy, and physical attributes.

The target variable is `potential`. The selected features are used to train separate regression models for each player group.

Player roles are assigned based on their listed positions. Players with multiple positions are assigned to the first matching role according to the implemented classification rules.

### 4. Position-Based Modeling

The project uses position-based regression models to investigate whether player attributes have different predictive relationships with potential across playing roles.

Players are categorized into three groups: forwards, midfielders, and defenders. A separate Random Forest Regressor is trained for each group using a role-specific feature set.

Goalkeepers are identified by the position-classification function but are not included in the current model evaluation. Separate goalkeeper and winger models are potential extensions for future work.

### 5. Model Training and Evaluation

A Random Forest Regressor is trained separately for forwards, midfielders, and defenders.

For each group, the data is split into training and testing sets using an 80/20 ratio and random_state=42. Predictions are evaluated using three regression metrics:

| Metric | Interpretation |
|---|---|
| MAE | Average absolute prediction error, measured in rating points |
| RMSE | Penalizes larger prediction errors more heavily |
| R² | Measures the proportion of target variance explained by the model |

The metrics are used together to evaluate prediction accuracy and compare model performance across positions.

## 📊 Model Evaluation

| Player role | MAE | RMSE | R² |
|---|---:|---:|---:|
| Forwards | 1.57 | 2.12 | 0.88 |
| Midfielders | 1.66 | 2.19 | 0.87 |
| Defenders | 1.68 | 2.27 | 0.84 |


## 🚀 Getting Started

### Prerequisites

Install Python and Git. A virtual environment is recommended to keep project dependencies isolated.

### 1. Clone the repository

```bash
git clone https://github.com/Wizzeman/fifa_players_potential_prediction.git
cd fifa_players_potential_prediction
```

### 2. Create a virtual environment

```bash
python -m venv .venv
```

Activate it on Windows:

```bash
.venv\Scripts\activate
```

On macOS or Linux:

```bash
source .venv/bin/activate
```

### 3. Install dependencies

If the repository includes a `requirements.txt` file:

```bash
pip install -r requirements.txt
```

Otherwise, install the core libraries:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

### 4. Run the analysis

Start Jupyter Notebook:

```bash
jupyter notebook
```

Open the relevant notebook and execute the cells in order, beginning with data loading and preprocessing.

## 🔮 Future Improvements

Potential extensions to this project include:

- Comparing additional regression algorithms, such as Random Forest, Gradient Boosting, XGBoost, and CatBoost.
- Using cross-validation and systematic hyperparameter tuning.
- Comparing position-specific models with a single general-purpose model.
- Evaluating feature importance and model interpretability.
- Investigating the effect of including or excluding `overall_rating`.
- Improving goalkeeper predictions through specialized features.
- Building a reusable Scikit-learn preprocessing and modeling pipeline.
- Developing a simple application that predicts potential for a selected player.

## ⚠️ Limitations

- Predictions depend on the quality, coverage, and consistency of the dataset.
- FIFA potential ratings are the target labels, not guaranteed measures of a player's real-world future performance.
- Position-specific models may have less training data available than a general model.
- Feature leakage, inappropriate preprocessing, or unrepresentative train-test splits can lead to overly optimistic evaluation results.
- Model performance should be assessed on held-out data and compared against appropriate baselines.

## 📜 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

The project license applies to the project's original code and does not automatically grant redistribution rights for third-party datasets or other external materials.

## 👨‍💻 Author

**Mohamad (Wizzeman)**

Computer Engineering student interested in Data Science, Machine Learning, and practical data-driven projects.

- GitHub: [@Wizzeman](https://github.com/Wizzeman)
- Repository: [FIFA Player Potential Prediction](https://github.com/Wizzeman/fifa_players_potential_prediction)

---

If you find this project useful, feel free to ⭐ the repository or contribute ideas for further improvements.
