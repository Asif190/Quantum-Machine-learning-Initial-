# Variational Quantum Classifier (VQC) for Iris Classification

![Quantum Machine Learning](https://img.shields.io/badge/Quantum-Machine%20Learning-blueviolet)
![Qiskit](https://img.shields.io/badge/Qiskit-1.3.0-6464ff)
![Python](https://img.shields.io/badge/Python-3.8+-blue)
![License](https://img.shields.io/badge/License-MIT-green)

## 🚀 Project Overview

This project implements a **Variational Quantum Classifier (VQC)** using **Qiskit 1.0+** to perform binary classification on the Iris dataset (Setosa vs. Versicolour). It demonstrates a complete hybrid quantum-classical machine learning workflow, including quantum feature encoding, trainable parameterized quantum circuits (ansatz), classical optimization, and NISQ (Noisy Intermediate-Scale Quantum) device simulation.

### 🎯 Key Features

- **Hybrid Quantum-Classical Approach**: Combines quantum circuits for feature processing with classical optimization
- **Multiple Ansatz Implementations**: Compares `TwoLocal` and `EfficientSU2` architectures
- **NISQ Noise Simulation**: Realistic quantum noise modeling using depolarizing errors and readout errors
- **Classical Baseline**: SVM comparison to contextualize quantum performance
- **Performance Analysis**: Visual comparison of quantum, classical, and noisy quantum models
- **Optimized for Kaggle**: Runs efficiently within Kaggle's free GPU environment

## 📊 Results

| Model | Accuracy | Notes |
|-------|----------|-------|
| **SVM (Classical)** | 100% | Perfect separation on binary Iris |
| **VQC (EfficientSU2)** | ~65-80% | Best performing quantum model |
| **VQC (TwoLocal)** | ~43-65% | Sensitive to initialization |
| **VQC (NISQ Noisy)** | ~5-15% lower | Realistic quantum hardware simulation |

> **Note**: Results vary due to random initialization of quantum circuit parameters. The EfficientSU2 ansatz generally outperforms TwoLocal for this dataset.

## 🧠 Technical Architecture

### Quantum Circuit Design

1. **Feature Map**: `ZZFeatureMap` with linear entanglement encodes classical data into quantum states
2. **Ansatz**: `EfficientSU2` (recommended) or `TwoLocal` creates trainable quantum circuits
3. **Optimizer**: COBYLA (Constrained Optimization BY Linear Approximation)
4. **Simulator**: Qiskit Aer for noiseless and noisy simulation

### NISQ Noise Model

- **1-Qubit Depolarizing Noise**: 1% probability
- **2-Qubit Depolarizing Noise**: 2% probability
- **Readout Error**: 1% probability

## 🛠️ Installation

### Local Setup

```bash
# Clone the repository
git clone https://github.com/yourusername/quantum-ml-classifier.git
cd quantum-ml-classifier

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

qiskit==1.3.0
qiskit-aer==0.15.0
qiskit-machine-learning==0.7.2
qiskit-algorithms==0.3.0
numpy>=1.21.0
scikit-learn>=1.0.0
matplotlib>=3.3.0
