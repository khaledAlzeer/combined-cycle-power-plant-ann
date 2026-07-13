# Power Plant Energy Output Prediction using Artificial Neural Network (ANN)

A deep learning regression project that predicts the net hourly electrical energy output of a Combined Cycle Power Plant using an Artificial Neural Network built with TensorFlow/Keras.

---

## 📌 Overview

This project uses real-world sensor data (`Folds5x2_pp.xlsx`) collected from a Combined Cycle Power Plant over **6 years (2006–2011)**, containing **9,568 observations**, to train an Artificial Neural Network (ANN) that predicts the plant's **net hourly electrical energy output (PE)** based on ambient environmental conditions.

The project includes **feature scaling using StandardScaler**, ensuring that all input features are standardized before training the neural network, which improves training stability and helps the model converge more efficiently.

Unlike classification problems, this is a **regression task** — the model predicts a continuous numerical value (power output in MW) rather than a class label.

---

# 📊 Dataset

The dataset (`Folds5x2_pp.xlsx`) contains four continuous input features and one continuous target variable, collected while the power plant was operating at full load.

| Variable | Role | Description | Range | Unit |
|---|---|---|---|---|
| AT | Feature | Ambient Temperature | 1.81 – 37.11 | °C |
| V | Feature | Exhaust Vacuum | 25.36 – 81.56 | cm Hg |
| AP | Feature | Ambient Pressure | 992.89 – 1033.30 | millibar |
| RH | Feature | Relative Humidity | 25.56 – 100.16 | % |
| PE | Target | Net hourly electrical energy output | 420.26 – 495.76 | MW |

### Dataset Information

- **Instances:** 9,568
- **Features:** 4
- **Target Variable:** PE
- **Missing Values:** None
- **Problem Type:** Regression

---

# ⚙️ Tech Stack

- Python 3
- NumPy
- Pandas
- Matplotlib
- Seaborn
- Scikit-learn
- TensorFlow / Keras
- OpenPyXL

---

# ✨ Features

- Artificial Neural Network for Regression
- TensorFlow / Keras implementation
- Feature Scaling using `StandardScaler`
- Correlation Heatmap analysis
- Training and Validation Loss visualization
- Actual vs Predicted comparison
- Residual error analysis
- Regression evaluation using:
  - R² Score
  - MAE
  - RMSE

---

# 🧭 Workflow

1. Import required libraries.
2. Load the dataset.
3. Explore feature correlations.
4. Split the dataset into training and testing sets.
5. Apply Feature Scaling using `StandardScaler`.
6. Build the Artificial Neural Network.
7. Train the model.
8. Evaluate the model using regression metrics.
9. Visualize the model performance.

---

# 🔧 Data Preprocessing

The preprocessing steps include:

### 1. Train/Test Split

The dataset is divided into:

- **80% Training Data**
- **20% Testing Data**

### 2. Feature Scaling

`StandardScaler` is applied to the input features:

- AT
- V
- AP
- RH

The scaler is fitted **only on the training data** and then applied to both training and testing sets to avoid **data leakage**.

The target variable (`PE`) is **not scaled**, allowing the model to output predictions directly in the original unit (MW).

Feature scaling helps the ANN:

- Converge faster during training.
- Improve optimization stability.
- Prevent large-scale features from dominating the learning process.

---

# 🧠 Model Architecture

The Artificial Neural Network is built using TensorFlow/Keras Sequential API.

## Architecture

```
Input Layer
      |
Dense Layer (6 neurons, ReLU)
      |
Dense Layer (6 neurons, ReLU)
      |
Output Layer (1 neuron, Linear)
```

### Compilation

- **Optimizer:** Adam
- **Loss Function:** Mean Squared Error (MSE)

### Training Configuration

- **Epochs:** 100
- **Batch Size:** 32
- **Validation Split:** 20%

---

# 📈 Results & Evaluation

Since this is a regression problem, classification metrics such as accuracy and confusion matrix are not suitable.

The model is evaluated using:

| Metric | Description |
|---|---|
| R² Score | Measures how much variance in the target is explained by the model |
| MAE | Average absolute prediction error in MW |
| RMSE | Penalizes larger prediction errors more heavily |

## Model Performance

- **R² Score:** ~0.91
- **MAE:** ~4.0 MW
- **RMSE:** ~5.0 MW

The model explains approximately **91% of the variance** in the power output while maintaining relatively low prediction errors.

---

# 📊 Visualizations

The notebook includes:

## 1. Correlation Heatmap

Shows the relationships between input features and the target variable (PE).

## 2. Training & Validation Loss Curve

Displays how the Mean Squared Error changes over 100 epochs.

A logarithmic scale is used to clearly observe improvement during training.

## 3. Actual vs Predicted Scatter Plot

Compares:

- Actual power output values
- ANN predictions

The closer points are to the perfect prediction line, the better the model performs.

## 4. Residual Plot

Shows the prediction errors:

```
Residual = Actual Value - Predicted Value
```

A good model should have residuals randomly distributed around zero.

---

# 🚀 How to Run

## 1. Clone Repository

```bash
git clone https://github.com/khaledAlzeer/combined-cycle-power-plant-ann.git

cd combined-cycle-power-plant-ann
```

## 2. Install Dependencies

```bash
pip install numpy pandas matplotlib seaborn tensorflow scikit-learn openpyxl
```

## 3. Add Dataset

Make sure the dataset file exists:

```
Folds5x2_pp.xlsx
```

inside the project directory.

## 4. Run Notebook

```bash
jupyter notebook artificial_neural_network_regression.ipynb
```

---

# 📁 Project Structure

```
combined-cycle-power-plant-ann/
│
├── artificial_neural_network_regression.ipynb
├── Folds5x2_pp.xlsx
├── README.md
└── LICENSE
```

---

# 📓 Notebook Structure

```
Artificial Neural Network (Regression)

│
├── Importing the libraries
│
├── Part 1 - Data Preprocessing
│   ├── Importing the dataset
│   ├── Exploring Feature Correlations
│   ├── Splitting Dataset
│   └── Feature Scaling
│
├── Part 2 - Building the ANN
│   ├── Initializing the ANN
│   ├── Adding First Hidden Layer
│   ├── Adding Second Hidden Layer
│   └── Adding Output Layer
│
├── Part 3 - Training the ANN
│   ├── Compiling the Model
│   └── Training the Model
│
├── Part 4 - Prediction & Evaluation
│   ├── Making Predictions
│   └── Calculating R², MAE, RMSE
│
└── Part 5 - Visualization
    ├── Correlation Heatmap
    ├── Training Loss Curve
    ├── Actual vs Predicted Plot
    └── Residual Plot
```

---

# 📝 License

This project is licensed under the **MIT License**.

---

# 🙋‍♂️ Author

**Khaled Alzeer**

Software Engineering Student  
AI & Python Developer

⭐ Feel free to star the repository if you find it useful.
