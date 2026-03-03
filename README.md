# quantum-option-pricing-quandela-Qvolution2026
Hybrid Quantum Reservoir + Deep Neural Network model for multi-target financial time-series regression (224 Tenor outputs).

This project implements a high-accuracy hybrid Quantum Reservoir Computing (QRC) framework for forecasting swaption/option prices using:

Non-linear time embeddings

Quantum-inspired random feature projection

Deep neural readout network (SiLU activations)

Huber loss for financial robustness

Early stopping + LR scheduling
🚀 Project Overview

Financial derivative surfaces (such as swaption volatility grids) are high-dimensional, nonlinear, and seasonal.

This model combines:

Rich Time Feature Engineering

Linear trend

Polynomial trend

Yearly sinusoidal seasonality (sine + cosine)

Quantum-Inspired Reservoir Layer

Fixed nonlinear random projection

Sinusoidal transformation

Simulates quantum feature expansion under mode/photonic constraints

Deep Neural Readout

Fully connected layers

SiLU (Swish) activation

Dropout regularization

AdamW optimizer
🧠 Model Architecture
Time Features (4D)
        ↓
Quantum Reservoir (30D nonlinear expansion)
        ↓
Dense(128) + SiLU
        ↓
Dense(256) + SiLU
        ↓
Output Layer (224 Tenor Targets)
Loss Function: Huber Loss
Optimizer: AdamW
Scheduler: ReduceLROnPlateau
Early Stopping: Enabled
Project Structure
├── train.xlsx
├── test.xlsx
├── FINAL_AQORA_SUBMISSION.csv
├── best_qrc_model.pth
├── qrc_accuracy_final_plot.png
└── main.py

📊 Data Processing
Feature Engineering

From the Date column:

Convert to datetime

Compute Days Since Start

Create nonlinear embeddings:

𝑋
=
[
𝑡
,
𝑡
2
,
sin
⁡
(
2
𝜋
𝑡
/
365.25
)
,
cos
⁡
(
2
𝜋
𝑡
/
365.25
)
]
X=[t,t
2
,sin(2πt/365.25),cos(2πt/365.25)]

Targets are automatically extracted using:
