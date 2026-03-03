# quantum-option-pricing-quandela-Qvolution2026


📌 Overview

This project implements a high-dimensional regression model for the Aqora Option Pricing competition.

Goal:
Predict 224 Tenor-based option/swaption prices for future dates using historical time-series data.

The solution combines:

Nonlinear time feature engineering

Quantum-inspired reservoir mapping

Deep neural readout network

Robust financial loss (Huber)

Early stopping + LR scheduling

🧠 Method
1️⃣ Time Feature Engineering

From the Date column:

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

Captures:

Trend

Polynomial curvature

Annual seasonality

2️⃣ Quantum-Inspired Reservoir

Fixed nonlinear feature expansion:

class MerlinReservoir:
    def extract_features(self, x_batch):
        torch.manual_seed(42)
        random_projection = torch.randn(input_dim, 30)
        return torch.sin(x_batch @ random_projection) * np.pi

30 nonlinear features

Deterministic projection

Acts like a quantum kernel-style embedding

3️⃣ Neural Readout

Architecture:

Time Features (4D)
        ↓
Quantum Reservoir (30D)
        ↓
Dense(128) + SiLU
        ↓
Dense(256) + SiLU
        ↓
Output (224 Tenors)

Loss: HuberLoss
Optimizer: AdamW
Scheduler: ReduceLROnPlateau
Early Stopping: Enabled

📊 Outputs

Running the script generates:

best_qrc_model.pth – Best trained weights

qrc_accuracy_final_plot.png – Fit + forecast visualization

FINAL_AQORA_SUBMISSION.csv – Ready-to-upload submission file

▶️ How to Run
pip install pandas numpy torch scikit-learn matplotlib openpyxl
python main.py

Output:

✅ SUCCESS! FINAL_AQORA_SUBMISSION.csv ready to upload
