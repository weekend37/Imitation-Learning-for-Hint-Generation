# Smart Primer: Online Learning Hint Generation in an Imitation Learning Framework  

👩‍💻 **Authors:**  Helgi Hilmarsson, Dominik Damjakob, William Steenbergen, Emma Brunskill, Sherry Ruan  

---

## 📖 Overview
- **Goal**: Automate hint generation in online learning by mimicking expert teachers.  
- **Data**: 19 online conversations between children (ages 7–11) and a teacher, where children solved a geometry box-volume problem.  
- **Approach**:  
  - Represent student states using task progress, demographics, and conversation data.  
  - Train regression and classification models to predict which hint an expert teacher would give.  
- **Baseline**: Industry standard "increasing order" hints (simplest first, answer last).  
- **Result**: Models (especially linear regression) outperformed the baseline in both accuracy and mean absolute error.  

---

## 🧠 Methodology
### State Representation
Features were extracted from:
- Current sub-question (Q)  
- Previous hint (H)  
- Meta features (M): demographics, test scores, conversation stats  
- Bag-of-words encoding of messages (B)  
- Word2Vec embeddings (W) reduced via PCA  

### Models Tested
- Linear Regression  
- LASSO Regression  
- Logistic Regression (L1 penalty)  
- Random Forest  

### Evaluation
- **Accuracy**: % of hints correctly predicted compared to expert.  
- **MAE**: Average deviation from expert’s chosen hint.  
- **Validation**: Leave-One-Out Cross Validation (LOOCV) across children.  

---

## 📊 Key Results
- **Best Model**: Linear regression with Q+H+M+W features.  
  - Accuracy: **75%** (baseline = 65%)  
  - MAE: **0.30** (baseline = 0.48)  
- Regression models consistently outperformed classification models.  
- Word2Vec features added value despite limited dataset size.  
- Models learned to **skip hints** when appropriate, unlike the rigid baseline approach.  

---

## 🚀 Future Directions
- Expand dataset for more robust NLP features.  
- Predict both **timing** and **content** of hints (currently only content is modeled).  
- Explore reinforcement learning with rewards tied to student learning gains (e.g., pre/post test improvement).  
- Apply to broader educational contexts beyond geometry.  

---
