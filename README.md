# Engine Health Maintenance Prediction
## Overview
This project utilizes Machine Learning to predict the health status of aircraft engines. By analyzing sensor data and operational cycles, the model classifies engines into two categories: Safe or Needs Maintenance.

The solution uses a Random Forest Classifier to predict engine failure risk based on the Remaining Useful Life (RUL) derived from the NASA CMAPSS Turbofan Jet Engine Degradation Simulation data.

## 📊 Dataset
The notebook relies on a pre-processed dataset named train_FD001_prepared.csv.

Context: This data typically simulates jet engine degradation over time.

Input Features: The model utilizes operational cycles and specific sensor readings:

cycle

sensor2, sensor3, sensor4

sensor7, sensor8, sensor9

sensor15, sensor17, sensor20, sensor21

## 🎯 Objective
The goal is to perform Binary Classification to determine if an engine is approaching failure.

Label 0 (Safe): The engine has more than 30 cycles of remaining useful life.

Label 1 (Maintenance Needed): The engine has 30 or fewer cycles remaining before failure.

## 🛠️ Tech Stack
Language: Python 3.x

Libraries:

pandas (Data manipulation)

numpy (Numerical operations)

scikit-learn (Machine Learning modeling and metrics)

matplotlib & seaborn (Data visualization)

## ⚙️ Methodology
Data Loading & Cleaning:

Loads the dataset.

Removes rows containing missing (NaN) or infinite values to ensure data quality.

Features:

Selects the most relevant sensor columns based on domain knowledge or previous analysis.

Constructs the target variable (Label) by thresholding the RUL (Remaining Useful Life) at 30 cycles.

Model Training:

Splits data into Training (80%) and Testing (20%) sets.

Trains a Random Forest Classifier with 100 estimators.

Evaluation:

Calculates Accuracy, Precision, Recall, and F1-Score.

Generates a Confusion Matrix to visualize True Positives/Negatives.

Calculates and plots Feature Importance to identify which sensors contribute most to the prediction.

## 📈 Results
Based on the latest model execution:

Accuracy: 96.05%

Classification Report:

Class 0 (Safe): Precision 0.97 | Recall 0.98

Class 1 (Maintenance): Precision 0.88 | Recall 0.84

The model shows high reliability in distinguishing healthy engines from those requiring immediate attention.
