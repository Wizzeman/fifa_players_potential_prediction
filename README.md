# FIFA Player Potential Prediction ⚽

A machine learning project that predicts FIFA player potential ratings using player attributes, performance statistics, and player-specific characteristics. The project explores data preprocessing, exploratory data analysis, feature engineering, and regression modeling to estimate player potential and identify promising young players.

## 📌 Project Overview

Player potential is an important indicator of how much a football player can develop over time. However, predicting potential using only a player's current overall rating may not fully capture the differences between positions and individual player attributes.

This project aims to build machine learning models that predict player potential based on relevant features from a FIFA player dataset.

To account for differences between playing positions, the project explores **position-specific regression models** for four main player roles:

- **Forwards:** ST, CF
- **Wingers:** LW, RW, LM, RM
- **Midfielders:** CM, CDM, CAM
- **Defenders:** CB, RB, RWB, LB, LWB
- **Goalkeepers:** GK

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
| Attacking attributes | Finishing, dribbling, positioning, shot power |
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
- Examining missing values and duplicate records.
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

### 3. Feature Engineering

Feature engineering is used to create more informative representations of player characteristics.

Candidate engineered features include:

| Feature | Description |
|---|---|
| `growth_gap` | Difference between potential and overall rating |
| `value_efficiency` | A measure relating player value to rating or performance |
| `positions_count` | Number of positions listed for a player |
| `value_log` | Log-transformed representation of player market value |
| `young_underrated` | A feature designed to capture young players whose potential exceeds their current rating |
| `roles` | Grouping players according to their playing roles |
| `preferred_foot_binary` | Binary representation of preferred foot |

The exact definitions, transformations, and use of these features should be documented in the relevant notebook.

**Important:** Features must be selected according to the prediction objective. Since `growth_gap` is calculated using `potential`, it must not be used as an input feature when predicting `potential`. Doing so would introduce target leakage. It may instead be used for post-prediction analysis.

### 4. Position-Based Modeling

Football players have different attribute profiles depending on their roles. For example, finishing and positioning are particularly relevant to forwards, while tackling and interceptions are more relevant to defenders.

The project investigates separate regression models for different player roles rather than assuming that a single model will perform equally well for every position.

This approach allows model performance and relevant features to be compared across player groups.

### 5. Model Training and Evaluation

The dataset is prepared for training and testing, and regression models are trained to predict the target variable.

Model evaluation focuses on three metrics:

| Metric | Interpretation |
|---|---|
| MAE | Average absolute prediction error, measured in rating points |
| RMSE | Penalizes larger prediction errors more heavily |
| R² | Measures the proportion of target variance explained by the model |

The metrics are used together to evaluate prediction accuracy and compare model performance across positions.

## 📊 Model Evaluation

The following table can be completed with the final test-set results from each trained model.

| Player role | MAE | RMSE | R² |
|---|---:|---:|---:|
| Forwards | 1.57 | 2.12 | 0.88 |
| Midfielders | 1.66 | 2.19 | 0.87 |
| Defenders | 1.68 | 2.27 | 0.84 |

*Note: These results are placeholders, not measured model performance. Replace them with actual evaluation results before publishing.*

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
