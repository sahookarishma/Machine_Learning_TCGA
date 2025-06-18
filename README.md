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
