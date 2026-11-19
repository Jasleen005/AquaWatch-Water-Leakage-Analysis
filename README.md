# AquaWatch: Machine Learning-Based Water Leakage Analysis

## Project Overview

AquaWatch is a machine learning-based predictive analytics project that investigates patterns associated with recorded water leakage events in urban water distribution networks.

The project uses multisource SCADA telemetry data to explore how operational and environmental signals relate to leakage-event labels. It applies exploratory data analysis, supervised machine learning, dimensionality reduction, and clustering to evaluate the potential of data-driven approaches for water network monitoring.

**Note:** The target variable represents observations within a seven-day window of recorded leakage events. Therefore, this project investigates leakage-associated patterns rather than confirming an active leak at a specific timestamp.

## Objectives

- Analyse SCADA data from an urban water distribution network.
- Understand data quality, missing values, and temporal patterns.
- Investigate relationships between sensor measurements and recorded leakage-event labels.
- Build and compare multiple machine learning models.
- Apply PCA and K-Means clustering to explore the structure of the data.
- Evaluate model performance using multiple classification metrics.

## Dataset

The project uses an hourly multisource water infrastructure dataset containing operational and environmental measurements.

- **Total observations:** 8,737
- **Predictor features:** 18
- **Target variable:** `fault_d7`
- **Data frequency:** Hourly
- **Target interpretation:** Leakage-event association within a ±7-day window.

**Dataset source:**  
[Zenodo Dataset – DOI: 10.5281/zenodo.15096167](https://doi.org/10.5281/zenodo.15096167)

The dataset is not included in this repository. Please obtain it from the original source and follow its licensing and usage conditions.

## Methodology

The project follows these main stages:

1. **Data Understanding and EDA**
   - Dataset inspection and statistical summaries.
   - Missing-value analysis.
   - Target distribution and temporal analysis.
   - Visual exploration of sensor behaviour.

2. **Data Preprocessing**
   - Feature and target separation.
   - Chronological train-test splitting.
   - A 168-hour temporal gap between training and test periods.
   - Median imputation and feature scaling using training data.

3. **Machine Learning Models**
   - Logistic Regression
   - Decision Tree
   - Random Forest
   - Support Vector Machine (SVM)
   - Multi-Layer Perceptron (MLP)

4. **Dimensionality Reduction and Clustering**
   - Principal Component Analysis (PCA).
   - K-Means clustering.

5. **Model Evaluation**
   - Accuracy
   - Precision
   - Recall
   - F1-score
   - ROC-AUC
   - Average Precision
   - Log Loss
   - Confusion Matrix

## Initial Model Results

The following results were obtained on the chronological test set:

| Model | Accuracy | F1-score | ROC-AUC | Average Precision |
|---|---:|---:|---:|---:|
| Logistic Regression | 78.79% | 87.44% | 0.5511 | 0.8626 |
| Decision Tree | 78.68% | 87.68% | 0.5329 | 0.8547 |
| Random Forest | 84.52% | 91.37% | 0.6205 | 0.8805 |
| SVM | 72.20% | 82.30% | 0.5449 | 0.8344 |
| MLP | **86.12%** | **92.26%** | 0.5786 | **0.8808** |

The MLP achieved the highest accuracy and F1-score among the evaluated models, while Random Forest achieved the highest ROC-AUC.

However, the results require careful interpretation. The test set has a high positive-class proportion, and the models show limited ability to distinguish negative cases. A high F1-score alone does not establish reliable leakage detection.

## Current Limitations

- The dataset represents a particular water infrastructure environment.
- The target label indicates proximity to recorded leakage events, not necessarily an active leak.
- The temporal distribution of target classes differs between training and testing periods.
- The models produce a considerable number of false positives.
- The contribution and possible target association of pre-derived anomaly-score features require further investigation.
- The current results should not be interpreted as proof of real-world deployment readiness.

## Future Improvements

- Investigate potential information leakage in engineered anomaly-score features.
- Perform feature ablation experiments.
- Strengthen temporal validation.
- Improve false-positive control and probability calibration.
- Explore event-level evaluation where reliable event timestamps are available.
- Add explainable AI techniques such as SHAP.
- Develop a dashboard for interpreting model predictions and sensor behaviour.

## Technologies Used

- Python
- Jupyter Notebook
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Machine Learning
- PCA and K-Means Clustering

## Repository Structure

```text
AquaWatch-Water-Leakage-Analysis/
│
├── AquaWatch.ipynb
├── README.md
└── (Additional project files will be added)
```

## How to Run

1. Clone this repository:

   ```bash
   git clone https://github.com/Jasleen005/AquaWatch-Water-Leakage-Analysis.git
   ```

2. Install the required Python libraries:

   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn jupyter
   ```

3. Download the dataset from the original Zenodo source.

4. Place the dataset in the appropriate project directory.

5. Open and run `AquaWatch.ipynb` using Jupyter Notebook.

## Project Status

**Current stage:** Initial model development and evaluation completed. Further validation, feature investigation, and model improvements are planned.

---

*Developed as an academic Predictive Analytics project.*
