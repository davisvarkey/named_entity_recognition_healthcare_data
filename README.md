# Identifying Entities in Healthcare Data

This project focuses on extracting and classifying medical entities—specifically diseases and treatments—from structured healthcare text using a Conditional Random Field (CRF) model. The goal is to build a custom Named Entity Recognition (NER) system that can predict treatments for given diseases based on labeled data.

## 📂 Project Overview
Objective: Predict treatments for diseases using CRF-based sequence labeling.

Approach: Preprocess raw word-level data, extract linguistic features, train a CRF model, and build a disease-treatment dictionary using custom NER.

## 🧹 Data Preprocessing
The dataset is formatted with one word per line. Sentences are separated by empty lines, and labels follow the same structure.

![Dataset format](images/treatment.png)

Step 1: Reconstruct full sentences and their corresponding labels from the raw format.

Step 2: Apply the same logic to both training and test datasets.

The image provided illustrates this transformation—from raw word-level input to structured sentence-label pairs.

## 🧠 Linguistic Feature Extraction
Using the spaCy NLP library:

Load sentences into a spaCy model.

Identify and list the top 25 most frequent NOUN or PROPN tokens.

For each word in a sentence, extract features such as:

Part-of-speech (POS) tag

Prefixes and suffixes

Previous word features

Word shape and casing

These features are used to construct X_train, X_test, Y_train, and Y_test datasets for model training.

## 🔍 Model Training: Conditional Random Field (CRF)
Model Type: CRF (discriminative probabilistic model for sequence labeling)

Training: Fit the CRF model using the extracted features and labels.

Evaluation: Predict labels on test data and assess performance using standard metrics (e.g., accuracy, F1-score).

## 🧬 Custom NER: Disease and Treatment Identification
Using the trained CRF model:

Predict Disease (D) or Treatment (T), or Others (O) sequences from  each sentence in the test set.

Construct a dictionary mapping diseases to their associated treatments.

Example Output:

{

  "Diabetes": ["Insulin", "Metformin"],

  "Hypertension": ["Amlodipine", "Lisinopril"]

}

Querying: Input a disease name to retrieve its corresponding treatments from the dictionary.