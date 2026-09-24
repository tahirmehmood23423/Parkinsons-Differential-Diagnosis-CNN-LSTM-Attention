# Parkinson's Differential Diagnosis with a Multi-Task CNN-LSTM-Attention Network

**MS Computer Science thesis, School of Electrical Engineering and Computer Science (SEECS), NUST Islamabad**

Supervisor: Prof. Qaiser Riaz

> 🚧 **The code is being uploaded.** The training notebooks, cross-validation scripts and evaluation figures will be added here soon.

## Overview

Parkinson's disease (PD) is often confused with other movement disorders that look similar. This project uses **wrist-worn inertial sensors (smartwatch accelerometers)** recorded during short, **seated fine-motor tasks**, and trains a single deep network to solve two problems together:

1. **Activity recognition:** which of 10 fine-motor activities the subject is doing
2. **Differential diagnosis:** whether the subject is a **Healthy Control (HC)**, has **Parkinson's Disease (PD)**, or has a **Differential Disorder (DD)**

## Method

| Stage | Details |
|---|---|
| Dataset | PADS: Parkinson's Disease Smartwatch Dataset (PhysioNet) |
| Input | Windows of tri-axial acceleration, 200 time steps × 3 axes (~288K windows) |
| Feature extractor | Conv (64) → Dropout → Conv (64) → Dropout → Max-Pool |
| Temporal model | LSTM (64 units) |
| Attention | 4-head self-attention over the LSTM sequence |
| Heads | Shared Dense (64) → two softmax heads: **10 activities** and **3 disease classes** |
| Evaluation | **Subject-level k-fold cross-validation** (no subject in both train and test), per-wrist experiments |
| Explainability | XAI attribution maps over the input signal |

**Activities:** CrossArms, DrinkGlas, Entrainment, HoldWeight, LiftHold, PointFinger, Relaxed, StretchHold, TouchIndex, TouchNose
**Disease labels:** 0 = Healthy, 1 = Parkinson's Disease, 2 = Differential Disorders

## Results (from the accompanying manuscript)

- **~94%** accuracy on ten-class fine-motor activity recognition
- **~91%** accuracy on the three-class HC / PD / DD task, despite class imbalance

## Planned repository structure

```
├── notebooks/        # Colab & Kaggle training notebooks
├── src/              # data loading, windowing, model, training loop
├── kfold/            # subject-level k-fold cross-validation (resume-capable)
├── results/          # confusion matrices, per-fold metrics, XAI figures
└── requirements.txt
```

## Tech stack

Python · TensorFlow / Keras · NumPy · scikit-learn · Matplotlib · Google Colab / Kaggle

## Related publication

*Differentiating Parkinson's Disease from Similar Neurological Disorders via Seated Fine Motor Activities and Wearable Inertial Sensors.* T. Mehmood et al. (manuscript in preparation for IEEE Sensors Journal)

## Author

**Engr. Tahir Mehmood**: MS CS @ NUST SEECS · BS Electrical Engineering @ NUST
[LinkedIn](https://www.linkedin.com/in/tahir-mehmood-596131209/) · tahirmehmoodrehmani@gmail.com
