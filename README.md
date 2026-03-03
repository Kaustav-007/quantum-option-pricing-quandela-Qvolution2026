# quantum-option-pricing-quandela-Qvolution2026



# Q-volution Hackathon 2026: Quantum Option Pricing with MerLin

## 🚀 Strategic Business Impact
This project addresses the "Computational Bottleneck" in real-time derivative pricing. Traditional Monte Carlo simulations struggle with the non-linear volatility of long-dated swaptions. By leveraging the high-dimensional feature mapping of Quandela’s photonics-based QPU, we reduce the classical training overhead while maintaining 224-column predictive accuracy. This provides financial institutions with a faster, hardware-efficient path to automated hedging.

## 🧠 The Hybrid Architecture
Our model utilizes a "Best of Both Worlds" approach:
1. **Quantum Reservoir (Perceval & MerLin):** A fixed quantum circuit acts as a non-linear feature extractor. It projects financial time-data into a quantum state, capturing complex market cycles.
2. **Classical Readout (PyTorch):** A deep neural network using **SiLU** activations and **Huber Loss** to translate quantum features into precise, outlier-resistant price forecasts.

## 📊 Model Accuracy & Forecasting
*(Model successfully fits historical swaption data and extrapolates into the 2051 test period.)*

![Forecast Accuracy](visuals/qrc_accuracy_final_plot.png) 
*Caption: Historical fit vs. 2051 target forecasts.*

## ⚙️ Hardware Readiness & Circuit Decomposition
To ensure the mathematical reservoir can be executed on physical hardware, we used Clements decomposition to compile the $8 \times 8$ unitary matrix into a native mesh of tunable Phase Shifters and Beam Splitters, strictly obeying the Ascella QPU constraints.

![Circuit Decomposition](visuals/quantum_circuit_decomposition.png)
*Caption: Photonic circuit decomposition of the Quantum Reservoir.*

## 🛠️ Setup & Usage
1. **Install Dependencies:**
   ```bash
   pip install merlinquantum perceval-quandela torch pandas scikit-learn
