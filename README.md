# Cervical Lesion Classification using HSV Features & XGBoost

Machine Learning project for **classifying pre-cancerous cervical lesion images** into three classes: **Milky, Opaque, and Transparent**.

The project combines lesion segmentation, HSV color analysis, dominant color extraction, and XGBoost classification to analyze visual characteristics of cervical lesions.

## 🎯 Objective

To develop a classification system that uses **HSV statistical features and dominant color features** to distinguish three cervical lesion classes.

## 📊 Dataset

The dataset consists of cervical lesion images organized by patient/case and classified into:

- **Milky**
- **Opaque**
- **Transparent**

The project applies **case-based splitting** to prevent images from the same patient/case from appearing in both training and testing data.

| Dataset | Cases | Images |
|---|---:|---:|
| Training | 97 | 303 |
| Testing | 25 | 83 |

Split ratio:

**80% Training — 20% Testing** :contentReference[oaicite:2]{index=2}

## 🔬 Methodology

```text
Cervical Lesion Images
        ↓
YOLO Lesion Segmentation
        ↓
Lesion-only Extraction
        ↓
Resize 224×224
        ↓
RGB → HSV
        ↓
Feature Extraction
        ↓
HSV Statistics + Dominant Color
        ↓
StandardScaler
        ↓
XGBoost Classifier
        ↓
Classification
```

## 🎨 Feature Extraction

A total of **15 numerical features** were extracted:

### HSV Statistical Features
- Hue Mean
- Hue Standard Deviation
- Saturation Mean
- Saturation Standard Deviation
- Value Mean
- Value Standard Deviation

### Dominant Color Features
Dominant colors were extracted using **K-Means clustering (k = 3)** in HSV space, producing 9 additional features:

- `Dom1_H`, `Dom1_S`, `Dom1_V`
- `Dom2_H`, `Dom2_S`, `Dom2_V`
- `Dom3_H`, `Dom3_S`, `Dom3_V`

:contentReference[oaicite:3]{index=3} :contentReference[oaicite:4]{index=4}

## 🤖 Model

**XGBoost Classifier**

Configuration:

```text
n_estimators = 100
learning_rate = 0.1
max_depth = 5
objective = multi:softmax
```

XGBoost was selected to model non-linear relationships among the extracted color features. :contentReference[oaicite:5]{index=5}

## 📈 Results

### Model Performance

| Model | Accuracy |
|---|---:|
| XGBoost | 43% |

Reported class-level performance:

| Class | Specificity | Sensitivity |
|---|---:|---:|
| Milky | 29% | 8% |
| Opaque | 52% | 59% |
| Transparent | 29% | 33% |

The model performed best on the **Opaque** class, while **Milky** and **Transparent** remained more difficult to distinguish. :contentReference[oaicite:6]{index=6}

## 🔎 Key Findings

- HSV and dominant-color features can capture important visual characteristics of cervical lesions.
- The **Opaque** class was the easiest class for the model to recognize.
- Classification errors mainly occurred between **Milky, Opaque, and Transparent** classes with similar color characteristics.
- The overlap of HSV distributions between classes indicates that color features alone may not be sufficient for all visually ambiguous cases.
- Additional features such as texture, vascular patterns, or more advanced approaches could improve classification robustness. :contentReference[oaicite:7]{index=7} :contentReference[oaicite:8]{index=8}

## 🛠️ Tech Stack

- Python
- OpenCV
- YOLO
- XGBoost
- Scikit-learn
- K-Means Clustering
- Pandas
- NumPy
- Matplotlib
- Seaborn

## 📚 Project Focus

**Computer Vision · Medical Image Processing · Color Feature Extraction · Machine Learning · Biomedical Imaging**

## 👨‍💻 Author

**Rafki Sahasika Riyuda**

Computer Systems Graduate  
AI / Machine Learning • Computer Vision • Data Analytics

📧 `rafkirafki551@gmail.com`

🔗 [LinkedIn](https://www.linkedin.com/in/rafkiSahasikaRiyuda)

---

⭐ Developed as part of the **Biomedical Image course project — Universitas Sriwijaya**.
