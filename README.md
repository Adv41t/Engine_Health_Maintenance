# Engine Health Maintenance Prediction
## Overview
This project utilizes Machine Learning to predict the health status of aircraft engines. By analyzing sensor data and operational cycles, the model classifies engines into two categories: Safe or Needs Maintenance.

The solution uses a Random Forest Classifier to predict engine failure risk based on the Remaining Useful Life (RUL) derived from the NASA CMAPSS Turbofan Jet Engine Degradation Simulation data.

## 📊 Dataset
The train_FD001_prepared.csv dataset is derived from the NASA CMAPSS (Commercial Modular Aero-Propulsion System Simulation) project. This is a standard benchmark dataset for predictive maintenance.

Breakdown of what each sensor represents in a turbofan jet engine:

### 1. Operational Feature
Cycle: This acts as a timestamp. It represents the number of flights (or operational cycles) the engine has completed. The goal is to predict how many more cycles it can run before it fails (RUL).

### 2. Temperature Sensors (Monitoring Heat)
These measure the heat at various stages of the engine. A sudden rise usually indicates friction, poor airflow, or component degradation.

Sensor 2 (T24): Total Temperature at the LPC (Low-Pressure Compressor) Outlet.

Sensor 3 (T30): Total Temperature at the HPC (High-Pressure Compressor) Outlet.

Sensor 4 (T50): Total Temperature at the LPT (Low-Pressure Turbine) Outlet.

### 3. Pressure Sensors (Monitoring Stress)
These measure the internal pressure, which is critical for thrust generation. Drops in pressure often signal leaks or compressor stall.

Sensor 7 (P30): Total Pressure at the HPC (High-Pressure Compressor) Outlet.

### 4. Rotational Speed Sensors (Monitoring RPM)
These track how fast the engine shafts are spinning.

Sensor 8 (Nf): Physical Fan Speed (RPM).

Sensor 9 (Nc): Physical Core Speed (RPM).

### 5. Performance & Efficiency Sensors
These are complex calculated metrics that indicate overall engine health and efficiency.

Sensor 15 (BPR): Bypass Ratio. This is the ratio of air that goes around the engine core vs. the air that goes through the core. A shift here indicates fan or compressor issues.

Sensor 17 (htBleed): Bleed Enthalpy. This relates to the energy extracted from the compressor for airframe needs (like cabin pressure).

Sensor 20 (W31):HPT Coolant Bleed. The amount of air diverted to cool the High-Pressure Turbine.

Sensor 21 (W32): LPT Coolant Bleed. The amount of air diverted to cool the Low-Pressure Turbine.

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
