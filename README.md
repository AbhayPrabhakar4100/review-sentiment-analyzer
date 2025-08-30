# product-review-sentiment-ml

## 🚀 Overview
This project applies **machine learning techniques** to classify product reviews by sentiment.  
The objective is to predict whether a review is **positive** or **negative** using only its text content, and then compare predictions against the actual product ratings.  

By exploring multiple models, this project evaluates trade-offs in accuracy, precision, and recall to identify the most reliable classifier for sentiment prediction.

---

## 🗃 Dataset
- **File:** `product_reviews_with_sentiment.csv`  
- **Total Samples:** 34,627  
- **Columns:**  
  - `product_id` → product identifier (dropped)  
  - `product_rating` → rating on a 1–5 scale  
  - `product_review` → raw review text (main input feature)  
  - `Unnamed: 0` → index column (removed during preprocessing)  

---

## 📝 Preprocessing
- Removed unused columns (`Unnamed: 0`, `product_id`)  
- Filtered out neutral reviews (rating = 3)  
- Mapped ratings:  
  - Ratings 4 & 5 → **Positive (1)**  
  - Ratings 1 & 2 → **Negative (0)**  
- Addressed class imbalance using **SMOTE** (Synthetic Minority Over-sampling Technique)  

---

## 🔧 Methodology

### 1. Text Vectorization
- TF-IDF (max features: 5000)  
- English stop words removed  

### 2. Class Balancing
- Applied **SMOTE** on training data to equalize positive vs negative samples  

### 3. Models Trained
- Logistic Regression (SMOTE)  
- Random Forest (SMOTE)  
- XGBoost (SMOTE)  

---

## 📊 Results

| Model                | Accuracy | Recall (Neg) | Precision (Neg) | F1-Score (Neg) |
|----------------------|----------|--------------|-----------------|----------------|
| Logistic Regression  | **92.76%** | 69%         | 22%             | 33%            |
| Random Forest        | **97.34%** | 18%         | 48%             | 27%            |
| XGBoost              | **95.65%** | 48%         | 30%             | 37%            |

➡️ **Final Choice:** **XGBoost (SMOTE)**  
- Best trade-off between recall and precision for negative class  
- Outperforms Random Forest in recall and achieves stronger balance than Logistic Regression  

---

## 🛠 Libraries
- Python 3.x  
- NumPy, Pandas, Scikit-learn  
- imbalanced-learn (SMOTE)  
- XGBoost  

---

## 📄 License
This project was developed for academic purposes.  
Feel free to **star ⭐ or fork 🍴** if you find it useful!
