<div align="center">

<img src="powerplant-banner.svg" alt="Animated power plant banner" width="100%"/>

<br/>

![Status](https://img.shields.io/badge/status-paused-orange?style=for-the-badge)
![Model](https://img.shields.io/badge/model-ANN%20(PyTorch)-blueviolet?style=for-the-badge)
![Dataset](https://img.shields.io/badge/dataset-CCPP%20(UCI)-informational?style=for-the-badge)

</div>

Predicting the net hourly electrical energy output of a **Combined Cycle Power Plant (CCPP)** using an Artificial Neural Network (ANN) built with PyTorch.

> Status: Completed.

---

## Overview

A combined cycle power plant generates electricity using a combination of gas turbines, steam turbines, and heat recovery systems. Its output isn't constant — it fluctuates with ambient environmental conditions.

This project uses **4 years of hourly sensor data** to train a neural network that predicts the plant's **net electrical energy output (PE)** from four ambient measurements, helping approximate how weather conditions affect power generation.

---

## Dataset

The dataset (`powerplant_data.csv`) contains **9,568 hourly readings**, each with the following fields:

| Feature | Description | Unit |
|---------|--------------------------|--------|
| `AT` | Ambient Temperature | °C |
| `V` | Exhaust Vacuum | cm Hg |
| `AP` | Ambient Pressure | mbar |
| `RH` | Relative Humidity | % |
| `PE` | **Net Energy Output** (target) | MW |

- **Inputs:** `AT`, `V`, `AP`, `RH`
- **Output:** `PE`

---

## 🧠 Model Architecture

A simple feedforward ANN (Multi-Layer Perceptron) built in PyTorch:

```
Input (4 features)
      │
Linear(4 → 6) → ReLU
      │
Linear(6 → 6) → ReLU
      │
Linear(6 → 1)   →  Predicted PE
```

**Training setup**
- Loss function: `MSELoss`
- Optimizer: `Adam`
- Epochs: `100`
- Batch size: `32`
- Features standardized using `StandardScaler`
- Train/test split: `80% / 20%`

---

## 🗂️ Repository Structure

```
Power_Plant/
├── ANN_Regression.ipynb   # Data loading, preprocessing, model, training loop
├── powerplant_data.csv    # CCPP hourly sensor dataset (9,568 rows)
└── README.md              # You are here
```

---

## ⚙️ Getting Started

### Requirements
```bash
pip install pandas numpy scikit-learn torch
```

### Run
1. Clone the repo
   ```bash
   git clone https://github.com/Kushagra-2112/Power_Plant.git
   cd Power_Plant
   ```
2. Open `ANN_Regression.ipynb` in Jupyter or VS Code
3. Run all cells to preprocess the data, train the ANN, and view train/validation loss per epoch

---

## 📈 Roadmap

- [ ] Fix training loop bug (variable typo in loss logging)
- [ ] Fit `StandardScaler` on train set only, transform test set
- [ ] Add evaluation metrics (RMSE, R²) on the test set
- [ ] Plot predicted vs. actual energy output
- [ ] Compare ANN performance against baseline models (Linear Regression, Random Forest)
- [ ] Save trained model weights

---

## 📚 Dataset Credit

Based on the **Combined Cycle Power Plant Data Set** from the UCI Machine Learning Repository.

---

## 📄 License

No license specified yet.
