# 🌾 Crop Recommendation System

## 📌 Overview
The **Crop Recommendation System** is a machine learning-based application that recommends the most suitable crop based on soil nutrients and environmental conditions.

The system analyzes the following parameters:

- Nitrogen (N)
- Phosphorus (P)
- Potassium (K)
- Temperature
- Humidity
- Soil pH
- Rainfall
- Season

Using these inputs, the trained machine learning model predicts the **best crop to cultivate**.

---

# 🎯 Features

- Predicts the **best crop** for given soil conditions.
- Uses **multiple machine learning models** for comparison.
- Performs **Exploratory Data Analysis (EDA)** with visualizations.
- Includes **season-based crop prediction**.
- Uses **Random Forest Classifier** for final prediction.
- Model is saved using **Pickle** for deployment.
- Can be integrated into a **web application using Flask API**.

---

# 🗂 Dataset

The dataset contains agricultural and environmental parameters.

| Feature | Description |
|------|------|
| N | Nitrogen content in soil |
| P | Phosphorus content in soil |
| K | Potassium content in soil |
| temperature | Average temperature |
| humidity | Relative humidity |
| ph | Soil pH value |
| rainfall | Rainfall amount |
| season | Derived agricultural season |
| label | Recommended crop |

Dataset size:

- **2200 rows**
- **8+ features**

---

# 🌦 Season Feature Engineering

The dataset originally does not contain a season column.  
Season is derived using rainfall and temperature.

| Condition | Season |
|------|------|
| rainfall > 200 | Kharif |
| temperature < 25 | Rabi |
| otherwise | Zaid |

Example implementation:

```python
def get_season(row):
    if row['rainfall'] > 200:
        return "Kharif"
    elif row['temperature'] < 25:
        return "Rabi"
    else:
        return "Zaid"
```

---

# 🔎 Exploratory Data Analysis (EDA)

EDA is performed to understand the dataset.

### Steps performed:

- Dataset overview
- Missing value check
- Crop distribution analysis
- Histogram distribution of features
- Correlation heatmap
- Pairplot visualization
- Outlier detection using boxplots

Libraries used:

- Matplotlib
- Seaborn
- Pandas

---

# ⚙ Data Preprocessing

The following preprocessing steps are applied:

### 1. Season Encoding

Season is converted into numerical values using `LabelEncoder`.

Example:

```
Kharif → 0
Rabi → 1
Zaid → 2
```

### 2. Target Encoding

Crop labels are encoded using `LabelEncoder`.

### 3. Feature Scaling

Numerical features are standardized using `StandardScaler`.

### 4. Train-Test Split

Dataset split:

- **80% training**
- **20% testing**

---

# 🤖 Machine Learning Models

The following models were trained and evaluated:

| Model | Description |
|------|------|
| Logistic Regression | Linear classification model |
| Decision Tree | Tree-based classifier |
| Support Vector Machine | Maximum margin classifier |
| Naive Bayes | Probabilistic classifier |
| Random Forest | Ensemble learning model |

Random Forest achieved the **highest accuracy**, so it is used as the final model.

---

# 📊 Model Evaluation

Models are evaluated using:

- Accuracy Score
- Precision
- Recall
- F1 Score
- Classification Report

A bar chart is generated to compare model performance.

---

# 💾 Model Saving

The trained model and preprocessing objects are saved using **Pickle**.

```python
import pickle

pickle.dump(rf, open("crop_recc_model.pkl", "wb"))
pickle.dump(sc, open("crop_recc_scaler.pkl", "wb"))
pickle.dump(le, open("crop_recc_label_encoder.pkl", "wb"))
pickle.dump(season_encoder, open("season_encoder.pkl", "wb"))
```

Saved files:

```
crop_recc_model.pkl
crop_recc_scaler.pkl
crop_recc_label_encoder.pkl
season_encoder.pkl
```

These files are used in the web application backend.

---




# 🛠 Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn
- Flask
- Pickle

---



---


---

# 📜 License

This project is intended for **educational and research purposes**.
