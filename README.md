# Parkinson's Differential Diagnosis with a Multi-Task CNN-LSTM-Attention Network

**MS Computer Science thesis, School of Electrical Engineering and Computer Science (SEECS), NUST Islamabad**

Supervisor: Prof. Qaiser Riaz

> **Note:** The code is being uploaded. The training notebooks, cross-validation scripts and evaluation figures will be added here soon.

## Overview

Parkinson's disease (PD) is often confused with other movement disorders that look similar. This project uses **wrist-worn inertial sensors (smartwatch accelerometers)** recorded during short, **seated fine-motor tasks**, and trains a single deep network to solve two problems together:

1. **Activity recognition:** which of 10 fine-motor activities the subject is doing
2. **Differential diagnosis:** whether the subject is a **Healthy Control (HC)**, has **Parkinson's Disease (PD)**, or has a **Differential Disorder (DD)**

## Method

- **Dataset:** PADS, Parkinson's Disease Smartwatch Dataset (PhysioNet)
- **Input:** windows of tri-axial acceleration, 200 time steps x 3 axes (about 288K windows)
- **Feature extractor:** two convolutional layers (64 filters each) with dropout, followed by max pooling
- **Temporal model:** LSTM with 64 units
- **Attention:** 4-head self-attention over the LSTM sequence
- **Output heads:** shared dense layer (64 units) feeding two softmax heads, one for 10 activities and one for 3 disease classes
- **Evaluation:** subject-level k-fold cross-validation (no subject appears in both training and test data), with per-wrist experiments
- **Explainability:** XAI attribution maps over the input signal
- **Activities:** CrossArms, DrinkGlas, Entrainment, HoldWeight, LiftHold, PointFinger, Relaxed, StretchHold, TouchIndex, TouchNose
- **Disease labels:** 0 = Healthy, 1 = Parkinson's Disease, 2 = Differential Disorders

## Results (from the accompanying manuscript)

- About 94% accuracy on ten-class fine-motor activity recognition
- About 91% accuracy on the three-class HC / PD / DD task, despite class imbalance

## Planned Repository Structure

- notebooks: Colab and Kaggle training notebooks
- src: data loading, windowing, model and training loop
- kfold: subject-level k-fold cross-validation (resume-capable)
- results: confusion matrices, per-fold metrics and XAI figures
- requirements.txt

## Tech Stack

- Python, TensorFlow, Keras
- NumPy, scikit-learn, Matplotlib
- Google Colab, Kaggle

## Related Publication

- Differentiating Parkinson's Disease from Similar Neurological Disorders via Seated Fine Motor Activities and Wearable Inertial Sensors. T. Mehmood et al. Manuscript in preparation for IEEE Sensors Journal.

## Author

- Engr. Tahir Mehmood, MS Computer Science, NUST SEECS
- LinkedIn: [linkedin.com/in/tahir-mehmood-596131209](https://www.linkedin.com/in/tahir-mehmood-596131209/)
- Email: tahirmehmoodrehmani@gmail.com
