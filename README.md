## Model Evaluation Report

### Approach & Algorithms Used
For this project, we aim to classify whether an account is at risk (`bad_flag`) based on the given features. We use multiple machine learning models to compare their effectiveness. The models evaluated include:

- **Logistic Regression** – A simple yet effective linear classifier.
- **Random Forest Classifier** – A robust ensemble model using decision trees.
- **XGBoost** – A powerful gradient boosting algorithm optimized for structured data.
- **LightGBM** – A gradient boosting model designed for efficiency and speed.
- **CatBoost** – A boosting model that handles categorical features efficiently.

Each model was trained on the dataset and evaluated based on performance metrics.

---

## Steps Followed

### Data Loading & Exploration
- Loaded training and test datasets.
- Checked for missing values and overall data distribution.
- Verified class distribution of the target variable (`bad_flag`).

### Preprocessing
- Dropped rows where the target variable (`bad_flag`) was missing.
- Removed non-relevant columns such as `account_number`.
- Identified and dropped columns that were entirely empty.
- Imputed missing values using the median strategy.
- Standardized numerical features using `StandardScaler` for uniform scaling.

### Model Training & Evaluation
- Trained each model on the preprocessed dataset.
- Predicted class probabilities and labels.
- Evaluated models using the following metrics:
  - **AUC Score** – Measures how well the model distinguishes between classes.
  - **F1 Score (Class 0 & Class 1)** – Evaluates the balance between precision and recall.
  - **Classification Report** – Provides detailed precision, recall, and F1-score for both classes.

### Model Comparison & Selection
- Printed and compared the AUC scores of all models.
- Identified the model with the highest AUC score as the best-performing model.
- Provided a summary of the best model and its evaluation metrics.

---

## Key Insights & Observations
- The dataset contained missing values, requiring imputation to maintain integrity.
- Feature standardization helped ensure models performed optimally, especially Logistic Regression.
- Some models, like **XGBoost** and **LightGBM**, showed higher AUC scores, indicating better predictive performance.
- **Random Forest** performed well but was computationally expensive.
- **Logistic Regression** was the simplest model but had lower predictive power.
- **CatBoost** handled categorical variables efficiently but took longer to train compared to others.

---

## Metrics Used for Effectiveness
- **AUC Score** – Higher values indicate better model discrimination between good and bad accounts.
- **F1 Score** – Measures the balance between precision and recall for both classes.
- **Classification Report** – Provides a complete picture of model performance per class.

The best model was selected based on the highest **AUC Score**, ensuring optimal predictive capability.

---

## Feature Importance Visualization

### Overview
This visualization represents the **top 20 most important features** used in our machine learning model. Feature importance indicates the contribution of each feature in making predictions, helping us understand which attributes have the most significant impact on the model’s decision-making process.

### Graph Description
- **Title:** Top 20 Feature Importance
- **X-axis:** Importance score of each feature, representing its contribution to the model's predictions.
- **Y-axis:** Displays the **top 20 features** ranked in descending order of importance.

### Key Observations
- The `onus_attribute_2` feature has the highest importance score, meaning it plays the most significant role in the model's decisions.
- Other highly ranked features include `onus_attribute_17`, `onus_attribute_20`, and `onus_attribute_23`, indicating that the **onus_attribute** category is highly influential in this dataset.
- Several `bureau` features, such as `bureau_439`, `bureau_450`, and `bureau_430`, also contribute significantly, suggesting that attributes related to **bureau** have a strong impact on the model.

### Use Case
Feature importance helps in:
- **Feature Selection:** Removing less important features to improve model efficiency.
- **Model Interpretability:** Gaining insights into what influences the predictions.
- **Bias Detection:** Identifying if any specific category of features dominates the decision-making process.

---

## ROC Curve Visualization

### Overview
This plot represents the **Receiver Operating Characteristic (ROC) curves** for multiple machine learning models, illustrating their performance in distinguishing between positive and negative classes. The **Area Under the Curve (AUC) score** quantifies each model’s ability to discriminate between classes, with a higher AUC indicating better performance.

### Graph Description
- **Title:** ROC Curves for All Models
- **X-axis (False Positive Rate - FPR):** Represents the proportion of false positives out of all actual negatives.
- **Y-axis (True Positive Rate - TPR):** Represents the proportion of true positives out of all actual positives.
- **Diagonal Line (Dotted Line):** Represents a random classifier (AUC = 0.5). A good model’s curve should be above this line.

### Key Observations
- **Logistic Regression (AUC = 0.89):** Performs well but is slightly less effective compared to other models.
- **Random Forest (AUC = 1.00), XGBoost (AUC = 1.00), and LightGBM (AUC = 1.00):** These models achieve **perfect classification** (AUC = 1.00), indicating exceptional discrimination ability.
- **CatBoost (AUC = 0.95):** Performs well but is slightly less effective than XGBoost, LightGBM, and Random Forest.
- **Overall Trend:** Tree-based ensemble models (Random Forest, XGBoost, LightGBM) show **superior performance** compared to Logistic Regression and CatBoost.

### Use Case
ROC curves help in:
- **Comparing different classification models** to select the best-performing one.
- **Threshold tuning** to balance false positives and false negatives.
- **Evaluating model robustness** in detecting the positive class.

### Conclusion
This ROC curve visualization indicates that **ensemble models (Random Forest, XGBoost, and LightGBM) outperform other classifiers with an AUC of 1.00**. Logistic Regression, while still effective, has a lower AUC, and CatBoost performs slightly worse than other tree-based methods.

---

## Bad Flag Distribution
This bar chart shows the imbalance in the `bad_flag` variable, where **Class 0 (majority) has over 70,000 instances**, while **Class 1 (minority) is significantly underrepresented**. This imbalance may impact model performance, requiring techniques like **resampling** or **weighted loss functions** for better predictions.

---

## Analysis of F1 Scores for Each Model
This bar chart visualizes the **F1 scores** for different machine learning models, evaluated separately for **Class 0 (majority class)** and **Class 1 (minority class)**. 

### Observations:
- **Logistic Regression:**
  - Achieves a nearly **perfect F1 score for Class 0**, indicating high precision and recall for the majority class.
  - Performs **poorly for Class 1**, struggling to detect minority class instances.
- **Random Forest:**
  - Exhibits **well-balanced performance for both classes** with high F1 scores.
  - Effectively handles class imbalance compared to Logistic Regression.
- **XGBoost:**
  - Strong **F1 score for Class 0** and relatively good performance for Class 1.
- **LightGBM:**
  - Maintains a strong **F1 score for Class 0** but struggles significantly with Class 1.
- **CatBoost:**
  - Achieves a **high F1 score for Class 0** but underperforms for Class 1, indicating potential issues with class imbalance handling.

---

## Conclusion
The project successfully evaluated multiple machine learning models, with **XGBoost, LightGBM, and Random Forest** showing superior performance. Model selection was based on **AUC scores, F1 scores, and interpretability insights**.
