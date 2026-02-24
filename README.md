## **Neural Network for Pima Indians Diabetes Diagnosis**

### **1. Problem Overview**

The objective of this project is to develop a **deep learning model** capable of predicting diabetes based on specific diagnostic measurements. This is a **binary classification** task using the *Pima Indians Diabetes Database*.

**Classification Targets:**

* **Class 0 (Healthy):** No signs of diabetes.
* **Class 1 (Diabetic):** Positive diagnosis.

---

### **2. Technical Approach**

I implemented a standard machine learning pipeline tailored for deep learning performance:

#### **Data Preprocessing**

* **Handling Missing Values:** Cleaned the dataset to ensure zero null values.
* **Feature Scaling:** Used `StandardScaler` to normalize features (e.g., Insulin vs. Pregnancies) to a mean of 0 and a standard deviation of 1. This prevents larger numerical values from dominating the gradient updates.
* **Data Splitting:** Applied an **80/20 train-test split** with **stratification** to maintain consistent class proportions.

#### **Model Architecture**

The model is a **Sequential Neural Network** designed as follows:

| Layer | Neurons | Activation |
| --- | --- | --- |
| **Input** | 8 | N/A |
| **Hidden Layer 1** | 32 | ReLU |
| **Hidden Layer 2** | 16 | ReLU |
| **Output Layer** | 1 | Sigmoid |

* **Optimization:** Compiled using the **Adam** optimizer and **Binary Crossentropy** loss.
* **Regularization:** Implemented **Early Stopping** (monitoring `val_loss`) to prevent overfitting and restore the best weights.

---

### **3. Results & Findings**

The model successfully converged, providing a reliable baseline for clinical prediction.

* **Final Test Accuracy:** `73.38%`
* **Convergence:** Training reached peak performance at **Epoch 31** before Early Stopping was triggered.

#### **Key Metrics Analysis**

* **Clinical Sensitivity:** The model’s ability to correctly identify diabetic patients (Recall) is the most critical metric here.
* **Confusion Matrix Interpretation:**
* **True Negatives:** High performance in correctly identifying healthy patients.
* **False Negatives:** The model missed **25 cases** of diabetes. In a medical context, reducing this number is a priority to ensure patients receive necessary care.



> **Insight:** While a 73% accuracy is solid for a baseline neural network, the "False Negative" rate suggests that further tuning (such as adjusting the classification threshold or adding Dropout layers) could improve clinical safety.
