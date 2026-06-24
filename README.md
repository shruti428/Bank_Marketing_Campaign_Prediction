# Bank Marketing Campaign Prediction

A machine learning project that predicts whether a customer will subscribe to a term deposit based on demographic, economic, and marketing campaign data from a Portuguese banking institution. Multiple classification models were evaluated using cross-validation and hyperparameter tuning to identify the best-performing approach.

## Project Overview

This project aimed to predict whether a customer would subscribe to a term deposit using data from a Portuguese banking institution's direct marketing campaigns. The dataset contained demographic, economic, and campaign-related variables, with the target variable indicating whether a customer subscribed ("yes") or did not subscribe ("no").

## Dataset

The dataset used in this project is the **Bank Marketing Dataset** from the UCI Machine Learning Repository. It contains information on direct marketing campaigns conducted by a Portuguese banking institution, with the objective of predicting whether a customer will subscribe to a term deposit.

Dataset source:
https://archive.ics.uci.edu/ml/datasets/bank+marketing

## Exploratory Data Analysis (EDA) 
EDA revealed a highly imbalanced dataset, with approximately 89% of customers in the "no" class and only 11% in the "yes" class. Because of this imbalance, model evaluation focused not only on accuracy but also on F1-Macro, which provides a balanced assessment of performance across both classes.

## Baseline Model

A baseline model that predicted all customers as "no" achieved an accuracy of 89%, but failed to identify any subscribers, resulting in an F1 score of 0 for the minority class and a Macro F1 score of approximately 0.47. This demonstrated that accuracy alone was insufficient for evaluating model performance on an imbalanced dataset.

## Model Comparison

Four machine learning algorithms were developed and evaluated using 5-fold cross-validation:

* Logistic Regression
* K-Nearest Neighbors (KNN)
* Decision Tree
* Support Vector Machine (SVM)

Hyperparameter tuning was performed using GridSearchCV to optimize model performance.

The tuned Decision Tree model achieved the best overall performance with an F1-Macro score of **0.585**, outperforming:

| Model               | F1-Macro Score |
| ------------------- | -------------- |
| Decision Tree       | 0.585          |
| SVM                 | 0.514          |
| Logistic Regression | 0.511          |
| KNN                 | 0.467          |

The optimal Decision Tree used a maximum depth of 3 and a minimum leaf size of 1, indicating that a relatively simple model was sufficient to capture meaningful patterns in the data.

Compared with the baseline model, the tuned Decision Tree substantially improved the ability to identify both subscribers and non-subscribers, increasing the F1-Macro score from approximately 0.47 to 0.585.

## Key Findings

* The dataset was highly imbalanced, making F1-Macro a more appropriate evaluation metric than accuracy.
* The tuned Decision Tree outperformed all other evaluated models.
* A relatively simple tree structure was sufficient to achieve the best predictive performance.
* Decision Trees provided strong interpretability while maintaining balanced classification performance.

## Conclusion

The Decision Tree was selected as the final model due to its superior predictive performance, interpretability, and ability to balance classification performance across both classes. This model could help financial institutions improve marketing efficiency by identifying customers who are more likely to subscribe to term deposit products.

## Next Steps

* Evaluate ensemble methods such as Random Forest and XGBoost to further improve predictive performance.
* Be cautious when using the `duration` variable, as it is only known after a call is completed and may introduce target leakage in real-world deployment.

## Technologies Used

* Python
* Pandas
* NumPy
* Scikit-learn
* Matplotlib
* GridSearchCV
* Jupyter Notebook

## Repository Structure

```text
Bank-Marketing-Campaign-Prediction/
│
├── data/
│   └── bank-additional-full.csv
│
├── bank_marketing_campaign_prediction.ipynb
│
└── README.md
```

### File Descriptions

* **data/bank_full.csv** – Dataset containing customer demographic, economic, and campaign-related information used for model development.
* **bank_marketing_campaign_prediction.ipynb** – Jupyter Notebook containing data exploration, preprocessing, model training, hyperparameter tuning, and evaluation.
* **README.md** – Project overview, methodology, results, and future improvements.

