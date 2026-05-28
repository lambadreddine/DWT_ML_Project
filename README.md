# Intelligent Machinery Fault Diagnosis Using Discrete Wavelet Transform (DWT) and Machine Learning

This repository presents an end-to-end intelligent fault diagnosis pipeline for rotating machinery. Leveraging experimental vibration data acquired from a mechanical test rig, the project combines multi-level Discrete Wavelet Transform (DWT) feature extraction with advanced Machine Learning and Deep Learning classifiers to achieve automated fault identification.

---

## 🚀 Intelligent Diagnosis Pipeline Overview

The system processes raw, non-stationary time-series vibration signals through a structured machine learning pipeline to classify four distinct machine health states:

![Workflow](images/workflow_2.jpg)

1. **Data Acquisition:** Multi-class vibration signatures captured directly from the experimental test rig.
2. **Preprocessing:** Signal standardization (Normalization) followed by window-based data splitting (Segmentation).
3. **Time-Frequency Feature Extraction:** 5-Level Discrete Wavelet Transform (DWT) decomposition.
4. **Statistical Feature Engineering:** Computing 10 distinct mathematical metrics across all wavelet coefficients.
5. **Classification:** Automated state prediction using classical Machine Learning models and a Feedforward Neural Network (FNN).

---

## 📊 1. Multi-Class Health States

The diagnostic models are trained to classify the machinery condition into four highly distinct operational classes:
* **Healthy:** Baseline steady-state control group with nominal clearance.
* **Rotor Unbalance:** Low-frequency mass eccentricity structural anomaly.
* **Angular Misalignment:** Axisymmetric geometric coupling anomaly.
* **Outer-Race Fault:** High-frequency transient micro-shocks localized on the bearing outer race.

---

## ⚙️ 2. Preprocessing & Feature Engineering

### A. Preprocessing
* **Normalization:** Signals are scaled using Min-Max scaling to ensure uniform distribution, removing amplitude variations caused by differing operational speeds.
* **Segmentation:** Long-duration continuous time-series signals are divided into fixed-length windows (segments) to increase dataset size and prepare samples for localized feature tracking.

### B. Discrete Wavelet Transform (DWT) Decomposition
To capture transient anomalies buried in non-stationary signals, a **5-Level DWT Decomposition** is applied. This decomposes the signal into **Details Coefficients (D1 to D5)** representing high-frequency transients, and a **Final Approximation Coefficient (A5)** representing low-frequency trends.

### C. The 10-Dimensional Statistical Feature Matrix
For *each* coefficient level (D1–D5 and A5), the script automatically extracts **10 statistical time-domain features** to capture geometric shape variations, energy changes, and impulsive spikes:

* **Max / Min Value:** Extracted peak bounds.
* **Peak-to-Peak (PTP):** Total amplitude range ($X_{\text{max}} - X_{\text{min}}$).
* **Mean:** Central tendency of the signal segment.
* **Root Mean Square (RMS):** Overall energy trend of the frequency band.
* **Variance (Var) / Standard Deviation (SD):** Energy dispersion metrics.
* **Skewness:** Measures the asymmetry of the wave distribution profile.
* **Crest Factor:** Ratio of peak shocks to the root energy profile.
* **Kurtosis:** Essential indicator measuring the "spikiness" caused by bearing impact cracks.

All calculated features are compiled into a highly structured **Feature Matrix** used as the input layer for the classification algorithms.

---

## 🤖 3. Model Evaluation & Performance Metrics

The feature matrix was trained, validated, and tested across multiple machine learning architectures to evaluate comparative optimization:

* **Support Vector Machines (SVM):** Evaluated with various kernel parameters (Linear/RBF).
* **K-Nearest Neighbors (KNN):** Distance-based instance learning.
* **Naive Bayes (NB):** Probabilistic state categorization.
* **Random Forest (RF):** Ensemble decision tree architecture.
* **Feedforward Neural Network (FNN):** A multi-layer deep network optimized with backpropagation.

### 🏆 Benchmark Champion Results

Following extensive cross-validation, the **Feedforward Neural Network (FNN)** completely outperformed the classical models due to its superior capacity to map highly non-linear time-frequency combinations.

* **Top Average Classification Accuracy across different operation condition :** **99.7%**
* **Engineering Impact:** The network achieved near-flawless precision in separating low-frequency structural issues (Unbalance/Misalignment) from high-frequency bearing micro-shocks under varying noise levels.

---

## 🔒 Data Privacy & Compliance Notice

> ⚠️ **Data Confidentiality Notice:** *The raw sensor time-series datasets used throughout this machine learning research are bound by institutional confidentiality agreements governing the laboratory facilities. This repository contains the data processing pipelines, feature extraction code, model configurations, and performance statistics to validate intelligent engineering competencies while fully respecting property boundaries.*
