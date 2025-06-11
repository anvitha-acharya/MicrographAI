# MicrographAI: Early Detection of Parkinson’s Disease via Handwriting Analysis

MicrographAI is a machine learning and deep learning-based project aimed at detecting early signs of Parkinson’s Disease (PD) using handwriting samples - specifically spiral and meander drawings. The project gets its name from *micrographia*, a neurological symptom commonly associated with PD, characterized by abnormally small and cramped handwriting.

---

## 🧬 About Parkinson’s Disease & Micrographia

Parkinson’s Disease is a progressive neurodegenerative disorder that affects movement, often starting with subtle motor symptoms. One of the earliest and most visible signs is **micrographia**, where patients exhibit reduced handwriting size and increased irregularity. These changes are often detectable before more severe symptoms appear, making handwriting analysis a powerful, non-invasive diagnostic tool.

**Early detection** of PD enables timely medical intervention, slows disease progression, and improves patient quality of life.

---

## 📂 Dataset

We used the publicly available **[NewHandPD dataset](https://www.kaggle.com/datasets/claytonteybauru/spiral-handpd/data)** which contains:
- **736 images** in total: 
  - 368 spiral drawings (healthy and Parkinson)
  - 368 meander drawings
- **Class Distribution**:
  - Healthy: 72 subjects
  - Parkinson: 296 subjects

The dataset includes visually distinguishable handwriting samples labeled accordingly, enabling supervised learning.

---

## 🔍 Methodology

The project involves a **hybrid approach** combining both deep learning and handcrafted features:

### 🧼 Preprocessing
- Images resized to **128×128**
- Converted to **grayscale**
- **Normalized** pixel values to [0, 1]
- **Binary label encoding** (Healthy → 0, Parkinson → 1)
- **Stratified train-test split**

### 🧠 Feature Extraction
- A **custom Convolutional Neural Network (CNN)** was trained on spiral and meander images to learn deep spatial and texture features.
- Additionally, **Fractal Dimension (FD)** was computed using the **box-counting method** to quantify the complexity of the handwriting curves—especially useful in detecting irregularities characteristic of Parkinson’s Disease.

### 🔗 Feature Fusion
- CNN features and FD values were concatenated to form a **hybrid feature vector**.

### 🤖 Machine Learning Models
We trained several classifiers using:
- CNN features alone
- CNN + FD (hybrid) features

Models used:
- Logistic Regression
- Support Vector Machine (SVM)
- Random Forest
- XGBoost
- Voting Ensemble (SVM + RF + XGBoost)

---

## 📊 Results & Insights

Our experiments demonstrated that:
- **CNN + FD hybrid features** consistently outperformed CNN-only features.
- **XGBoost with hybrid features** achieved the **highest accuracy, precision, recall, and F1-score**.
- The addition of **fractal dimension** improved model robustness by capturing complexity beyond what the CNN could learn alone.

| Model              | Accuracy | Precision | Recall | F1-Score |
|-------------------|----------|-----------|--------|----------|
| CNN + SVM         | 85%      | 83%       | 86%    | 84%      |
| CNN + RF          | 88%      | 86%       | 89%    | 87%      |
| **CNN + FD + XGB**| **92%**  | **91%**   | **93%**| **92%**  |

---

## 🧾 Conclusion

**MicrographAI** presents a cost-effective, interpretable, and non-invasive approach for early Parkinson’s Disease detection using handwriting analysis. The combination of deep learning (CNN) and fractal geometry (FD) offers a powerful diagnostic aid, with potential real-world applications in telemedicine and clinical screening.

---
