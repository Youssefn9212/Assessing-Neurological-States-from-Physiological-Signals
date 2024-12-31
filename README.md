# Assessing Neurological States from Physiological Signals

This project focuses on assessing neurological states, including stress (physical, emotional, and cognitive), using machine learning techniques on physiological signals. By leveraging classification and clustering models, the project aims to develop accurate methods for identifying stress states and understanding their impact.

<p align="center">
  <img src="https://github.com/user-attachments/assets/0badfc7b-7012-45d4-a44e-c1fac8729d56" alt="Project Image">
</p>


---

### Project Contributors
- **Youssef Nakhla**
- **Zeina Kishk**
- **Hanya Sheikh**

---

### Table of Contents
1. [Introduction](#introduction)
2. [Dataset](#dataset)
3. [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
4. [Preprocessing](#preprocessing)
5. [Unified Pipeline](#unified-pipeline)
6. [Modeling](#modeling)
   - [Classification Models](#classification-models)
   - [Clustering Models](#clustering-models)
7. [Conclusion](#conclusion)

---

### **Introduction**

Stress significantly impacts physical, cognitive, and emotional well-being. Accurate detection of stress levels is essential for developing interventions to mitigate its effects. This project uses machine learning models to classify stress states based on physiological signals, such as electrodermal activity (EDA), heart rate (HR), acceleration, temperature, and oxygen saturation (SpO2). The objective is to create models that accurately categorize stress into four states:
1. **Relaxed**
2. **Cognitive Stress**
3. **Emotional Stress**
4. **Physical Stress**

---

### **Dataset**

The dataset used is the **Non-EEG Dataset for Assessment of Neurological Status** available on PhysioNet. It includes physiological data from 20 healthy subjects (11 males, 9 females) aged 21–28. Signals were recorded under various stress-inducing conditions, such as:
- **Physical stress:** Exercise
- **Cognitive stress:** Problem-solving tasks
- **Emotional stress:** Watching horror movies

The dataset contains 7 stages per subject, including relaxation and various stress states. Signals are provided in WFDB format, with annotations marking transitions between stages.

---

### **Exploratory Data Analysis (EDA)**

Exploratory analysis revealed significant relationships between signals and stress states:
- **Electrodermal Activity (EDA):** Higher values are associated with cognitive stress, while lower values indicate emotional or physical stress.
- **Heart Rate (HR):** Physical stress correlates with higher heart rates, followed by emotional and cognitive stress.
- **Oxygen Saturation (SpO2):** Remains relatively constant across stress states, with minor variations.

---

### **Preprocessing**

To ensure uniformity, preprocessing included:
1. **Signal Segmentation:** Divided signals into stages based on annotations.
2. **State Consolidation:** Combined similar stages into broader categories:
   - Relaxation stages into **Relaxed**
   - Mini-emotional stress and emotional stress into **Emotional Stress**
3. **Class Balancing:** Applied:
   - **Undersampling** for the relaxation class.
   - **SMOTE** for underrepresented classes (e.g., Cognitive Stress).
4. **Dimensionality Reduction:**
   - **Principal Component Analysis (PCA):** Reduced features to retain 95% variance.
   - **Sequential Feature Selection (SFS):** Selected features based on model performance.
   - **Recursive Feature Elimination (RFE):** Removed less significant features.

---

### **Unified Pipeline**

A unified pipeline was developed to streamline experimentation, allowing combinations of preprocessing, feature selection, and modeling to be tested efficiently.

---

### **Modeling**

#### **Classification Models**
Three classification models were tested:
1. **Support Vector Machine (SVM):** Effective for high-dimensional data.
   - **Best Results:** PCA preprocessing achieved 93.3% accuracy and F1 score.
2. **Multi-Layer Perceptron (MLP):** Modeled complex relationships.
   - **Best Results:** PCA preprocessing achieved 98.5% accuracy and F1 score.
3. **K-Nearest Neighbors (KNN):** Simple and robust for non-linear patterns.
   - **Best Results:** PCA preprocessing achieved 98.3% accuracy and F1 score.

#### **Clustering Models**
Unsupervised clustering methods were also tested:
1. **K-Means Clustering:** Accuracy: 27%
2. **Hierarchical Clustering:** Accuracy: 25%
3. **Spectral Clustering:** Accuracy: 15%

Clustering models struggled due to overlapping features across stress categories, even after dimensionality reduction.

---

### **Conclusion**

Classification models outperformed clustering models in accurately identifying neurological states. PCA proved the most effective preprocessing method, significantly enhancing accuracy and F1 scores. While clustering algorithms were less effective due to feature overlap, future work can explore advanced techniques to improve feature separability for unsupervised learning.

---
