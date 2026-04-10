#  Brain Tumor Detection using SVM + PCA

##  Overview

This project focuses on classifying brain MRI images into different tumor types using **Support Vector Machine (SVM)** with **Principal Component Analysis (PCA)** for dimensionality reduction.

The goal is to analyze how different SVM kernels and training data sizes affect model performance.

---

##  Dataset

The dataset consists of brain MRI images categorized into:

* No Tumor
* Pituitary Tumor
* Glioma Tumor
* Meningioma Tumor

Dataset: https://www.kaggle.com/datasets/sartajbhuvaji/brain-tumor-classification-mri

---

##  Methodology

1. **Image Preprocessing**

   * Converted to grayscale
   * Resized to 200 × 200
   * Normalized pixel values

2. **Feature Extraction**

   * Images flattened into vectors

3. **Dimensionality Reduction**

   * PCA applied with 98% variance retention

4. **Classification**

   * SVM with:

     * RBF Kernel
     * Linear Kernel

---
## Kernel Comparison: RBF vs Linear SVM
 Methodology

The Support Vector Machine (SVM) classifier was implemented using two different kernels:

RBF Kernel (default)
Linear Kernel

The dataset was preprocessed and reduced using Principal Component Analysis (PCA) retaining 98% variance.
The model was trained on the training dataset and evaluated on a separate testing dataset to avoid data leakage.

Results
Training Score of Rbf kernel: 0.9689895470383275
Testing Score of Rbf kernel: 0.7182741116751269
Training Score of linear kernel: 1.0
Testing Score of linear kernel: 0.7360406091370558


Explanation of Results

The difference in performance between the RBF and linear kernels is due to the nature of the data and the effect of PCA.

The RBF kernel maps data into a higher-dimensional space and is capable of handling complex, non-linear relationships.
The linear kernel assumes that the data is linearly separable and tries to find a straight decision boundary.

After applying PCA, the dataset becomes:

Less noisy
More structured
Closer to linearly separable

As a result:

The linear kernel performs slightly better because the simplified data no longer requires complex non-linear boundaries.
The RBF kernel may slightly overfit the training data, leading to slightly lower performance on unseen test data.
Conclusion (Kernel Comparison)
Linear kernel achieved better generalization in this case
PCA plays a key role in improving linear separability
Higher training accuracy does not always imply better performance

## Effect of Training Data Size on SVM
Methodology

The model was trained using different portions of the training dataset:

20%
40%
60%
80%

The testing dataset was kept fixed and completely separate.

Training Data (%)	RBF Accuracy	Linear Accuracy
20%	
accuracy score of rbf for 20.0% of data is: 0.39593908629441626
accuracy score of linear for 20.0% of data is: 0.3883248730964467

40%	
accuracy score of rbf for 40.0% of data is: 0.4137055837563452
accuracy score of linear for 40.0% of data is: 0.4289340101522843

60%	
accuracy score of rbf for 60.0% of data is: 0.4517766497461929
accuracy score of linear for 60.0% of data is: 0.4796954314720812	

80%	
accuracy score of rbf for 80.0% of data is: 0.550761421319797
accuracy score of linear for 80.0% of data is: 0.6091370558375635	

 Accuracy Plot

![alt text](image.png)

 Explanation of Trend

The performance of both SVM models improves as the amount of training data increases.

🔹 At 20% Training Data
The model has limited exposure to patterns
Leads to underfitting
Low accuracy and unstable predictions
🔹 At 40%–60% Training Data
Model starts learning meaningful patterns
Accuracy improves steadily
Better generalization
🔹 At 80% Training Data
Model has sufficient data
Learns decision boundaries effectively
Achieves highest accuracy

*Kernel Behavior
RBF Kernel
Handles complex patterns
Performance improves gradually
May fluctuate slightly
Linear Kernel
More stable
Performs well after PCA
Can outperform RBF in simplified datasets
Conclusion (Training Size)
Increasing training data improves model performance
Small datasets lead to underfitting
PCA + Linear SVM is effective for structured data
More data → better generalization

## Both kernels (RBF and Linear) were evaluated using:

Accuracy
F1-score
Sensitivity
Specificity

Results:

For rbf kernel:
Accuracy: 0.7182741116751269
F1 Score: 0.6839626831122175
Sensitivity (Recall): 0.7182741116751269
Specificity: 0.9043132611203875

Results for linear kernel:
Accuracy: 0.7360406091370558
F1 Score: 0.6928118205449822
Sensitivity (Recall): 0.7360406091370558
Specificity: 0.9099626668741501


##  Important Note

The test dataset was kept completely separate from the training dataset.
PCA was fitted only on training data and applied to test data to avoid data leakage.

---

##  Credits

* Original dataset and base idea inspired from:
  https://github.com/Adityathere/Brain-Tumor-Detection-Using-SVM


---

## 👨‍💻 Author

**Vineet-mig**
