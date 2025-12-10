# MoE-CFD Surrogate Model (Public V2)
Regime-Aware Mixture-of-Experts Surrogate for Aerodynamic Coefficient Prediction

This repository provides the public Version 2 implementation of a Regime-Aware Mixture-of-Experts (MoE) surrogate model for predicting aerodynamic drag (Cd) across three flow regimes: attached, near-stall, and post-stall.  
V2 expands the findings seen in V1 by introducing regime-aware training, expert–regime alignment analysis, and visual tools for interpretability.

---

## 1. Key Features

### Mixture-of-Experts Architecture
- Shared encoder with multiple expert heads  
- Gating network trained for both regression and regime classification  
- Multi-task loss:  
  - Loss = MSE(Cd) + lambda * CrossEntropy(regime)

### Expert Specialization Metrics
- Intersection-over-Union (IoU) between true regimes and gating assignments  
- Measures how well experts align with physical flow regimes

### Visualization Tools
- 2D gating maps (angle of attack vs Reynolds number)  
- 3D expert-assignment scatter plots  
- Per-regime error distribution plots

### Ablation Experiments
- Number of experts tested: 2, 3, 5  
- Regularization values tested: 0.0, 0.1, 0.5, 1.0  
- Evaluated using validation MSE and IoU

### Reproducible Implementation
- PyTorch-based  
- Deterministic seeds  
- Modular, readable code  
- Notebook-friendly for experimentation

---

## 2. Repository Structure

```
moe-cfd-surrogate-Public-V2/
├── notebooks/
│   ├── moe_cfd_v2_training.ipynb
│   └── visualization_tools.ipynb
│
├── models/
│   ├── moe_model.py
│   └── utils.py
│
├── data/
│   └── synthetic_cfd_multi_regime.npz
│
├── results/
│   ├── gating_maps/
│   ├── ablation/
│   └── regime_errors/
│
└── README.md
```

---

## 3. Summary of V2 Results

### Best Configuration for Interpretability
- Number of experts: 3  
- Regularization lambda: 0.1  
- Average IoU: 0.927  

### Expert–Regime Alignment
- Expert 0: attached flow  
- Expert 1: post-stall flow  
- Expert 2: near-stall nonlinear zone  

### Best Accuracy Configuration
- Number of experts: 5  
- lambda = 0.1  
- Validation MSE: approximately 5.05e-4  

### Per-Regime Test Errors

| Regime      | MSE       | MAE       | Accuracy |
|-------------|-----------|-----------|----------|
| attached    | 1.25e-4   | 8.78e-3   | 0.995    |
| near-stall  | 9.16e-4   | 1.47e-2   | 0.996    |
| post-stall  | 8.14e-4   | 1.58e-2   | 0.993    |

---

## 4. How to Run

### Install dependencies
```
pip install -r requirements.txt
```

### Train the model
Open the notebook:
```
notebooks/moe_cfd_v2_training.ipynb
```

### Generate visualizations
Run:
```
notebooks/visualization_tools.ipynb
```

Outputs will appear in:

```
results/gating_maps/
results/regime_errors/
```

---

## 5. Citation

If this work is used in research or publications, please cite:

Apichet Janya  
"Regime-Aware Mixture-of-Experts Surrogate for Multi-Regime CFD"  
Version: Public V2, 2025  

---

## 6. License
MIT License.  
Free for academic, educational, and research use.  
Commercial use requires permission from the author.

---

## 7. Contact
Author: Apichet Janya  
Email: apichet.janya@cheetahinsurancebroker.com  
Location: Bangkok, Thailand
