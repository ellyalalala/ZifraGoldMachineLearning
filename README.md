# ZifraGoldMachineLearning

Recovery of gold from ore
Prepare a prototype of a machine learning model for Digital. The company develops solutions for the efficient operation of industrial enterprises.

The model must predict the recovery rate of gold from gold ore. Use data with mining and purification parameters.

The model will help optimize production so as not to launch an enterprise with unprofitable characteristics.

You need:

Prepare data;
Conduct exploratory data analysis;
Build and train the model.
To complete the project, use the pandas, matplotlib, and sklearn libraries. Their documentation will help you.


# 🪙 Gold Ore Recovery Prediction

## 📋 Project Description
This project develops a machine learning prototype for **Zifra Digital** to predict the gold recovery rate from ore based on mining and purification parameters.  

The model helps optimize production and avoid launching unprofitable facilities.

**Goal:** predict gold recovery rates at different processing stages to improve efficiency.

---

## 📂 Data

We used three datasets:  
- `gold_recovery_train_new.csv` — training set  
- `gold_recovery_test_new.csv` — test set  
- `gold_recovery_full_new.csv` — full dataset with reference values  

Each dataset includes measurements at flotation and final purification stages, metal concentrations (Au, Ag, Pb), process parameters, and target recovery rates.

---

## 🧪 Approach

### 🔷 Data Preparation
- Converted date column to `datetime`
- Checked duplicates and missing values
- Examined sample sizes and missing columns in the test set

### 🔷 Data Analysis
- Verified the correctness of `rougher.output.recovery`, calculated MAE relative to dataset values
- Identified features unavailable in the test set and their purpose
- Analyzed how the concentration of metals (Au, Ag, Pb) changes at different stages
- Compared the distribution of feed particle size between train and test (no significa

- **Key findings:**
- Gold share increases at each purification stage
- Anomalous values were removed to improve prediction quality

### 🔷 Modeling
✅ Trained and evaluated:
- Linear regression  
- Decision tree  
- Random forest  

✅ Models evaluated using cross-validation with sMAPE metric

✅ Chose **random forest** model with parameters:

{'max_depth': 1, 'n_estimators': 6}

✅ Tested on the test set

✅ Compared to a dummy (constant) model

### 📈 Results

| Model                | Validation sMAPE | Test sMAPE |
|-----------------------|------------------|------------|
| Linear Regression     | ~10.06%         | –          |
| Decision Tree         | ~11.04%         | –          |
| Random Forest         | **7.53%**       | **9.26%** |
| Dummy Model           | –               | 9.82%      |

🎯 Final test prediction: **Random Forest, sMAPE = 9.26%**  
The model outperformed the dummy baseline, confirming its adequacy.


📊 Conclusion

Analysis of metal concentrations showed that gold concentration significantly increases at each stage of ore processing. During the analysis of the total concentration of substances at different stages, anomalies were identified and removed to improve the quality of future predictive models. Based on the distribution, these anomalies were likely outliers.

On the training data, models of linear regression, decision tree, and random forest were trained and evaluated. As a result, the Random Forest model was selected for further prediction, with optimal parameters:

{'max_depth': 1, 'n_estimators': 6}

This model achieved a validation sMAPE of 7.53%.

Final testing on the test dataset showed that the selected Random Forest model successfully predicted the target gold concentration at the flotation and final purification stages, achieving a test sMAPE of 9.26%.

A baseline constant (mean prediction) model was also evaluated for adequacy check, which achieved a worse sMAPE of 9.82% on the test data.

_______

🚀 How to Run
1️⃣ Clone the repository:
git clone https://github.com/ellyalalala/ZifraGoldMachineLearning.git
cd ZifraGoldMachineLearning
2️⃣ Install dependencies:
pip install -r requirements.txt
3️⃣ Run the notebook:
jupyter notebook ZifraGoldML.ipynb

_______

🛠 Tech Stack:

Python 3.x

pandas, NumPy

matplotlib, seaborn

scikit-learn
