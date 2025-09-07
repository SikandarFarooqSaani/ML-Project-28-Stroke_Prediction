# 🧠 Stroke Prediction  

![Brain Logo](https://img.icons8.com/emoji/96/brain.png)  

---

## 📌 Project Overview  
This project is about predicting the likelihood of a **stroke** using patient data.  
The dataset is **highly imbalanced** ⚠️ (majority of patients have no stroke), which made training models quite tricky.  
Even without advanced imbalance handling yet, I explored multiple models, tuning, and ensembles to see how they perform.  

---

## 📂 Dataset  
📊 **Dataset Link:** [Stroke Prediction Dataset](https://www.kaggle.com/datasets/fedesoriano/stroke-prediction-dataset)  

- Class distribution:  
  - **0 (No Stroke): 4861 samples**  
  - **1 (Stroke): 249 samples**  
- Very **imbalanced dataset** ❌  
- Dropped irrelevant columns  
- Encoded categorical columns  

---

## ⚙️ Tech Stack & Libraries  
- **Python** 🐍  
- **NumPy, Pandas** → Data handling  
- **Scikit-learn** → Models, Cross-validation, RandomizedSearchCV  
- **Matplotlib, Seaborn** → Visualization  

---

## 🚀 Models & Experiments  

### 🔹 Logistic Regression  
- Accuracy → **0.93**  
- After RandomizedSearchCV → **0.95** ✅  
- Confusion Matrix showed **62 False Positives**  
<img width="649" height="547" alt="28-1" src="https://github.com/user-attachments/assets/065c9423-d9af-4dd7-8539-cd5468d718ea" />
<img width="649" height="547" alt="28-2" src="https://github.com/user-attachments/assets/24018688-90f9-47dd-bed0-9acdda7ee8ce" />

---

### 🔹 K-Nearest Neighbors (KNN)  
- Accuracy → **0.9344**  
- With RandomizedSearchCV → **0.955** 🏆  
- Confusion Matrix: performed better but imbalance still visible  
<img width="649" height="547" alt="28-3" src="https://github.com/user-attachments/assets/3eeef915-ba55-41b5-b336-4378fd94be01" />
<img width="649" height="547" alt="28-4" src="https://github.com/user-attachments/assets/3983d922-bde9-4083-9767-ef444f670a7c" />

---

### 🔹 Decision Tree  
- Accuracy → **0.90**  
- RandomizedSearchCV with class weights → **0.88**  
- Had **23 False Negatives** (bad for medical predictions ⚠️)  

<img width="649" height="547" alt="28-5" src="https://github.com/user-attachments/assets/1105c9f0-9904-447a-87e0-18c853598de3" />
<img width="649" height="547" alt="28-6" src="https://github.com/user-attachments/assets/9c665a8c-8673-45c1-838c-9df64d3a0756" />

---

### 🔹 Voting Classifier (LogReg + KNN + DT)  
- Used tuned hyperparameters from RandomizedSearchCV  
- Accuracy → **0.93**  
- Confusion Matrix: 960 TP, 62 FP, **no FN or TN**  
<img width="649" height="547" alt="28-7" src="https://github.com/user-attachments/assets/a8d8f58f-1fb7-4cff-9f4b-ff61da88ba70" />

---

### 🔹 Bagging  
- Accuracy → **0.93**  
- Confusion Matrix: similar misclassification trend  
<img width="649" height="547" alt="28-8" src="https://github.com/user-attachments/assets/39d8a1f6-5a93-46af-b666-fa162bfab3e8" />

---

### 🔹 AdaBoost  
- Accuracy → **0.939**  
- Confusion Matrix: fewer FP, but imbalance impact remained  
<img width="649" height="547" alt="28-9" src="https://github.com/user-attachments/assets/b3e2acfe-b65a-4cea-9de5-ed7bcf7a0307" />

---

### 🔹 Random Forest (RSCV)  
- Accuracy → **0.93**  
- Same TP/FP values as earlier models  
<img width="649" height="547" alt="28-10" src="https://github.com/user-attachments/assets/cf10e20f-cef3-438e-a6aa-ad3cd952de4c" />

---

### 🔹 Gradient Boosting  
- Accuracy → **0.93**  
- Confusion Matrix: had **1 FN and 1 TN**  
<img width="649" height="547" alt="28-11" src="https://github.com/user-attachments/assets/23459b31-9be5-4794-8355-665d5259bb4d" />

---

## 📊 Results  

| Model                          | Accuracy | Notes |
|--------------------------------|----------|-------|
| Logistic Regression            | 0.93     | Baseline |
| Logistic Regression (RSCV)     | **0.95** ✅ | 62 FP |
| KNN                            | 0.9344   | |
| KNN (RSCV)                     | **0.955** 🏆 | Best so far |
| Decision Tree                  | 0.90     | Weak on imbalance |
| Decision Tree (RSCV)           | 0.88     | 23 FN |
| Voting Classifier               | 0.93     | Balanced |
| Bagging                        | 0.93     | |
| AdaBoost                       | 0.939    | Strong |
| Random Forest (RSCV)           | 0.93     | |
| Gradient Boosting              | 0.93     | 1 FN, 1 TN |

---

## 💡 Key Takeaways  
- Dataset imbalance is the **biggest challenge** here ⚠️  
- Logistic Regression and KNN with **RandomizedSearchCV** performed the best (≈95%+) 🎯  
- Decision Trees struggled more due to imbalance  
- Ensemble methods (Voting, Bagging, Boosting) stabilized results but did not fix imbalance  
- **False Negatives are critical in medical predictions** — even small FN values are concerning  

---

## 🎯 Conclusion  
This project gave me insights into:  
- How imbalance can **mislead accuracy** (high accuracy but bad recall on minority class)  
- How different classifiers behave under imbalance  
- Importance of **hyperparameter tuning** (major score jumps!)  
- Next step → learn and apply **imbalance handling techniques** like:  
  - SMOTE / Oversampling  
  - Class weights  
  - Precision-Recall metrics instead of just accuracy  

---

✨ *Even small improvements matter when predicting something as serious as strokes.* ❤️‍🩹  
