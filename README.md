# Hydrogen–Methane Detection & Concentration Estimation (CNN + ML)

This project detects and classifies gas mixtures containing **Hydrogen (H₂)** and **Methane (CH₄)**, while also estimating their concentrations using **Convolutional Neural Networks (CNNs)** and traditional machine learning models.

It combines **spectral image analysis**, **deep learning regression**, and **classification models** to predict both gas concentration and mixture type from spectral data.

---

## 🧠 Project Overview

### 1️⃣ Data Preprocessing
- Loads a dataset containing Hydrogen, Methane, and Argon concentration spectra.
- Scales and reshapes the data into **2D spectral maps (50×90)** for CNN input.
- Defines target values: `H_ppm` and `Meth_ppm` (hydrogen and methane concentrations).

The dataset (`H2_CH4_dataset.xlsx`) used for model training is too large for GitHub upload (≈220 MB).  
You can download it from: [Google Drive / Share Link Here]  
Place it in the project root directory before running the script.

### 2️⃣ CNN Regression
- **Goal:** Predict gas concentrations (`H_ppm`, `Meth_ppm`)
- **Input:** 50×90×1 spectral maps
- **Architecture:**
  - 3 × `Conv2D + MaxPooling2D` blocks
  - `Flatten` → `Dropout(0.25)` → `Dense(256)` → `Dense(1)`
- **Optimizer:** Adam(1e-3)  
- **Loss Function:** Mean Squared Error (MSE)  
- **Metrics:** R² Score  
- **Training:** 100 epochs, 20% validation split  
- **Output Models:**  
  - `hydrogen_conc.h5`  
  - `methane_conc.h5`

### 3️⃣ Classification Models
- Classifies samples into one of four mixture categories:
  - **Hydrogen Only**
  - **Methane Only**
  - **Hydrogen and Methane**
  - **No Hydrogen No Methane**
- Algorithms used:
  - **Random Forest**
  - **K-Nearest Neighbors (KNN)**
- Evaluated via confusion matrices and accuracy reports.

### 4️⃣ Visualization
- **Spectral Heatmaps & 3D Surface Plots** (using Plotly)
- **Box, Violin, and Histogram Plots** (using Seaborn)
- **Confusion Matrices** (for model comparison)

---

## 📊 Results Summary

| Model | Task | Accuracy / R² | Notes |
|--------|------|---------------|-------|
| **CNN (Hydrogen)** | Regression | R² ≈ 0.98 | Excellent generalization |
| **CNN (Methane)** | Regression | R² ≈ 0.97 | Stable performance |
| **Random Forest** | Classification | ≈ 99% | Most robust mixture classifier |
| **KNN** | Classification | ≈ 98% | Slightly lower generalization |

---

## 🗂 Project Structure

```
hydrogen-methane-detection/
│
├── hydrogen-methane-detection.py   # Main pipeline (CNN + ML)
├── README.md                       # Project documentation
├── requirements.txt                # Dependencies
├── figures/                        # Optional: saved plots
└── models/                         # Optional: saved CNN models (.h5)
```

---

## ⚙️ Installation

Clone the repository:
```bash
git clone https://github.com/<your-username>/hydrogen-methane-detection.git
cd hydrogen-methane-detection
```

Install dependencies:
```bash
pip install -r requirements.txt
```

---

## 🚀 Usage

Run the main pipeline:
```bash
python hydrogen-methane-detection.py
```

After training:
- CNN models are saved as `hydrogen_conc.h5` and `methane_conc.h5`
- Confusion matrices and plots are generated automatically.

---

## 🔬 Key Libraries
- **TensorFlow/Keras** – CNN construction and training  
- **Scikit-learn** – ML classification models and metrics  
- **Plotly** – Interactive heatmaps and 3D surface visualization  
- **Matplotlib/Seaborn** – Statistical plotting  
- **OpenPyXL** – Excel file reading  

---

## 🧾 Requirements

All dependencies are listed in `requirements.txt`. Install via:
```bash
pip install -r requirements.txt
```

---

## 👨‍💻 Author
**Adeoluwa Oyinlola**  
Applied AI & Data Science | Machine Learning Researcher  

---

## 🪪 License
This project is licensed under the [MIT License](https://opensource.org/licenses/MIT).
