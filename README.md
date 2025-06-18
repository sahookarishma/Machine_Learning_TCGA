# Machine_Learning_TCGA
🔬 Multi-Omics Based Cancer Classification Using Machine Learning

This repository contains the implementation of machine learning models for classifying colorectal cancer (CRC) samples using transcriptomics and methylomics data obtained from the TCGA-GDC portal. The study involves pre-processing, feature selection, handling class imbalance, and applying supervised ML classifiers to identify cancerous vs. non-cancerous samples.
📁 Dataset Source

    Transcriptomics Data: TCGA-COAD gene expression profiles (68,575 genes × 699 samples)

    Methylomics Data:

        Illumina 27K (16,384 features × 861 samples)

        Illumina 450K (16,384 features × 861 samples)

Data was downloaded from the GDC Data Portal.
🧪 Methodology
🔹 1. Class Imbalance Handling

    CRC data shows significant imbalance:

        Transcriptomics: 648 tumor vs. 51 normal samples.

        Methylomics: 742 tumor vs. 119 normal samples.

    Applied oversampling (preferred) and undersampling methods:

        RandomUnderSampler

        TomekLinks

        RandomOverSampler

        ✅ SMOTE (Synthetic Minority Oversampling Technique) – best performance.

🔹 2. Feature Selection

    Applied LASSO (Least Absolute Shrinkage and Selection Operator) for reducing dimensionality.

    Parameters: alpha = 0.0013, max_iter = 5000

    Result: 1,421 significant features retained across omics platforms.

🔹 3. Classification Models

Built using scikit-learn and TensorFlow:

    Random Forest (RF): Ensemble model using majority voting from decision trees.

    K-Nearest Neighbors (KNN): Non-parametric model with Euclidean distance metric.

    Artificial Neural Network (ANN):

        Multi-layer feedforward network.

        Custom architecture defined by dataset covariates and class labels.

        Trained using backpropagation and activation functions.

📊 Results
🔬 Transcriptomics Data (TCGA-CRC)

| Class    | Model         | Precision | Recall | F1-score | Support |
| -------- | ------------- | --------- | ------ | -------- | ------- |
| Normal   | Random Forest | 1.00      | 1.00   | 1.00     | 135     |
| Tumor    | Random Forest | 1.00      | 1.00   | 1.00     | 124     |
| Accuracy | Random Forest | -         | -      | **1.00** | 259     |
|          |               |           |        |          |         |
| Normal   | KNN           | 0.99      | 1.00   | 1.00     | 135     |
| Tumor    | KNN           | 1.00      | 0.99   | 1.00     | 124     |
| Accuracy | KNN           | -         | -      | **1.00** | 259     |


🧬 DNA Methylation Data – Illumina 450K
| Class    | Model         | Precision | Recall | F1-score | Support |
| -------- | ------------- | --------- | ------ | -------- | ------- |
| Normal   | Random Forest | 1.00      | 1.00   | 1.00     | 81      |
| Tumor    | Random Forest | 1.00      | 1.00   | 1.00     | 83      |
| Accuracy | Random Forest | -         | -      | **1.00** | 164     |
|          |               |           |        |          |         |
| Normal   | KNN           | 0.99      | 1.00   | 0.99     | 81      |
| Tumor    | KNN           | 1.00      | 0.99   | 0.99     | 83      |
| Accuracy | KNN           | -         | -      | **0.99** | 164     |


🧬 DNA Methylation Data – Illumina 27K
| Class    | Model         | Precision | Recall | F1-score | Support |
| -------- | ------------- | --------- | ------ | -------- | ------- |
| Normal   | Random Forest | 1.00      | 1.00   | 1.00     | 68      |
| Tumor    | Random Forest | 1.00      | 1.00   | 1.00     | 65      |
| Accuracy | Random Forest | -         | -      | **1.00** | 133     |
|          |               |           |        |          |         |
| Normal   | KNN           | 1.00      | 1.00   | 1.00     | 68      |
| Tumor    | KNN           | 1.00      | 1.00   | 1.00     | 65      |
| Accuracy | KNN           | -         | -      | **1.00** | 133     |


🧠 Key Takeaways

    Random Forest consistently achieved 100% accuracy across all datasets.

    KNN also performed extremely well with accuracy between 99% and 100%.

    These results validate the effectiveness of preprocessing, class balancing using SMOTE, and robust feature selection using LASSO.

    The models are highly reliable for distinguishing tumor vs. normal samples in CRC.


PUBLICATION:
Sahoo K, Sundararajan V. IL-1β and associated molecules as prognostic biomarkers linked with immune cell infiltration in colorectal cancer: an integrated statistical and machine learning approach. Discov Oncol. 2025 Feb 28;16(1):252. doi: 10.1007/s12672-025-01989-3. PMID: 40019680; PMCID: PMC11871282.


