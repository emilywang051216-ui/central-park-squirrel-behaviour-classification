# Central Park Squirrel Behaviour Classification

A machine learning project that predicts squirrel–human interaction behaviour in Central Park using behavioural, spatial, temporal, and environmental features.

The project classifies squirrel interactions into three categories:

- Approach
- Indifferent
- Runs From

## Project Overview

This project investigates whether squirrel–human interaction behaviour can be predicted using observed activity, vocalisation, tail movement, location, time, and local squirrel density.

The complete workflow includes:

- data cleaning and preprocessing
- exploratory data analysis
- target construction
- feature engineering
- model training
- cross-validation
- model evaluation
- feature importance analysis

## Research Question

To what extent can squirrel–human interaction behaviour be predicted using behavioural, spatial, temporal, and environmental features, and which factors have the greatest influence on these interactions?

## Project Structure

```text
central-park-squirrel-behaviour-classification/
├── README.md
├── squirrel_behaviour_classification.ipynb
├── requirements.txt
├── data/
│   ├── squirrel.csv
│   ├── hectare.csv
│   └── stories.csv
└── results/
    ├── interaction_distribution.png
    ├── behaviour_correlation_heatmap.png
    ├── activity_score_boxplot.png
    ├── spatial_distribution.png
    ├── model_performance_comparison.png
    └── feature_importance.png
```

The complete analysis is contained in:

```text
squirrel_behaviour_classification.ipynb
```

## Dataset

The project uses three datasets:

- `squirrel.csv`
- `hectare.csv`
- `stories.csv`

The datasets are merged using shared fields including:

- `Hectare`
- `Shift`
- `Date`

Before running the notebook, place all required datasets inside the `data/` directory.

## Workflow

### 1. Import Libraries

The project uses the following Python libraries:

- pandas
- NumPy
- matplotlib
- seaborn
- SciPy
- scikit-learn

### 2. Load and Merge Data

The three source datasets are loaded and merged into a single DataFrame using common identifiers such as hectare, observation shift, and date.

### 3. Data Cleaning

The data-cleaning process includes:

- removing duplicate observations
- handling missing numerical and categorical values
- converting dates into datetime format
- cleaning invalid coordinates and height values
- converting Boolean variables into binary values
- checking inconsistent or unexpected values

Numerical missing values are handled using median imputation where appropriate. Missing categorical values are represented using an `Unknown` category.

### 4. Target Construction

The prediction target is stored in:

```text
Interaction_Type
```

It contains three possible classes:

- `Approach`
- `Indifferent`
- `Runs From`

The target is constructed from the original squirrel–human interaction indicators.

### 5. Feature Engineering

Several derived features are created to represent squirrel behaviour and spatial context.

Examples include:

- `Activity_Score`
- `Vocalisation_Score`
- `Tail_Activity`
- `Squirrel_Density_Level`
- north–south spatial zone
- east–west spatial zone
- temporal features derived from date and observation shift

The cleaned dataset may be exported as:

```text
A2_cleaned_full_dataset.csv
```

## Exploratory Data Analysis

The exploratory analysis examines:

- interaction class distribution
- behavioural correlations
- activity levels across interaction classes
- spatial patterns
- squirrel density
- relationships between engineered features and the target variable

Generated visualisations include:

- bar charts
- correlation heatmaps
- boxplots
- scatterplots
- spatial distribution plots

Example output files include:

```text
step5_interaction_distribution.png
step5_behaviour_correlation_heatmap.png
step5_activity_score_boxplot.png
step5_spatial_distribution.png
```

## Feature Preparation

Before model training, the data is prepared using:

- stratified train-test splitting
- one-hot encoding for categorical variables
- standardisation for distance-based and linear models
- separate preprocessing pipelines for different model types

`StandardScaler` is applied to Logistic Regression and K-Nearest Neighbours.

Preprocessing transformations are fitted using the training data only to reduce data leakage.

## Machine Learning Models

The following classification models are compared:

- Logistic Regression
- K-Nearest Neighbours
- Decision Tree
- Random Forest

The main evaluation metrics include:

- accuracy
- precision
- recall
- weighted F1 score
- confusion matrix

Five-fold cross-validation is used to compare model performance more reliably.

## Model Results

| Model | Mean Cross-Validation Weighted F1 |
|---|---:|
| Decision Tree | 0.438 |
| Logistic Regression | 0.471 |
| K-Nearest Neighbours | 0.592 |
| Random Forest | 0.618 |

Random Forest achieved the strongest overall weighted F1 score.

The results indicate that:

- Random Forest handled nonlinear relationships effectively
- KNN also achieved relatively strong performance
- `Runs From` and `Indifferent` were frequently confused
- the `Approach` class had fewer observations
- spatial and behavioural features contributed useful predictive information

### Model Performance Comparison

![Model Performance Comparison](step8_model_performance_comparison.png)

## Feature Importance

Random Forest feature importance is used to:

- identify the most influential predictors
- compare the full feature set with a reduced feature set
- investigate whether similar performance can be achieved using fewer variables

Example output files include:

```text
step8_model_performance_comparison.png
step9_top_feature_importance.png
```

## Requirements

The project requires Python 3 and the following libraries:

```text
pandas
numpy
matplotlib
seaborn
scipy
scikit-learn
jupyter
```

Install the required packages using:

```bash
pip install pandas numpy matplotlib seaborn scipy scikit-learn jupyter
```

Alternatively, create a `requirements.txt` file and run:

```bash
pip install -r requirements.txt
```

## Running the Project

1. Clone or download the repository.

2. Enter the project directory:

```bash
cd central-park-squirrel-behaviour-classification
```

3. Place the datasets inside the `data/` directory.

4. Open the notebook:

```bash
jupyter notebook squirrel_behaviour_classification.ipynb
```

5. Restart the kernel and run all cells in order.

Generated figures and processed datasets will be saved automatically.

## Key Findings

- Random Forest achieved the highest mean weighted F1 score.
- KNN performed better than Logistic Regression and Decision Tree.
- Spatial and behavioural features were useful for prediction.
- Interaction classes were not equally represented.
- `Runs From` and `Indifferent` showed substantial overlap.
- Model performance may be improved through further class balancing and hyperparameter tuning.

## Limitations

- The target classes are imbalanced.
- Some behavioural variables are sparse.
- The dataset represents one park and a limited observation period.
- The models identify statistical associations rather than causal relationships.
- Results may not generalise to squirrels in other environments or cities.

## Future Improvements

Possible improvements include:

- class weighting or resampling
- more extensive hyperparameter tuning
- repeated cross-validation
- additional weather features
- more detailed time-of-day information
- clustering before classification
- evaluation on data from other parks
- investigation of additional spatial features

## Technologies

- Python
- pandas
- NumPy
- scikit-learn
- matplotlib
- seaborn
- Jupyter Notebook

## Author

Yiqing Wang

University of Melbourne
