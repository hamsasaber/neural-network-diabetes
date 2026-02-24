Neural Network for Pima Indians Diabetes Diagnosis
1. Problem Overview
The objective of this project is to develop a deep learning model capable of predicting whether or not a patient has diabetes based on specific diagnostic measurements.

The dataset used is the Pima Indians Diabetes Database from Kaggle. This is a binary classification problem where the model must distinguish between two classes:

0 (Healthy): No signs of diabetes.

1 (Diabetic): Positive diagnosis.

2. Approach
To ensure the model performed effectively, I followed a standard machine learning pipeline adapted for neural networks:

Data Preprocessing:

Handling Missing Values: I cleaned the dataset to ensure no null values interfered with training.

Feature Scaling: Since features like "Insulin" (max ~800) and "Pregnancies" (max ~17) exist on vastly different scales, I used StandardScaler. This normalized the data to a mean of 0 and a standard deviation of 1, preventing the model from being biased toward features with larger numerical values.

Data Splitting: I used an 80/20 split for training and testing, employing stratification to ensure the ratio of diabetic to non-diabetic patients remained consistent across both sets.

Model Architecture:

I built a Sequential Neural Network with:

Input Layer: 8 neurons (matching the 8 clinical features).

Hidden Layer 1: 32 neurons with ReLU activation.

Hidden Layer 2: 16 neurons with ReLU activation.

Output Layer: 1 neuron with a Sigmoid activation function to output a probability between 0 and 1.

Optimization: The model was compiled using the Adam optimizer and Binary Crossentropy loss.

Early Stopping: To prevent overfitting, I implemented an Early Stopping callback that monitored val_loss and restored the best weights when the model stopped improving.

3. Results & Findings
The model successfully met the assignment's expected accuracy range.

Final Test Accuracy: 73.38%

Training Behavior: The model reached its peak performance at Epoch 31 before Early Stopping triggered. The training curves show a steady decline in loss, indicating the model was learning patterns rather than just memorizing data.

Key Metrics Analysis:
Recall for Diabetes: The model's ability to "catch" diabetic patients is critical in a medical context. With an accuracy of ~73%, the model provides a solid baseline, though it remains conservative in its predictions.

Confusion Matrix Interpretation:

True Negatives: High performance in identifying healthy patients.

False Negatives: There were 25 cases where the model missed a diabetic diagnosis. In a real-world clinical setting.
