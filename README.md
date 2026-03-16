📊 Telecom Customer Churn Prediction (Machine Learning)

A Machine Learning project that predicts whether a telecom customer is likely to churn (leave the service) using historical customer usage data.
The model helps telecom companies identify high-risk customers and take proactive retention actions.

🚀 Project Overview

Customer churn is a major challenge in the telecom industry. Acquiring new customers costs significantly more than retaining existing ones.

This project builds a predictive Machine Learning model that identifies customers likely to churn so businesses can:

Reduce customer churn

Improve retention strategies

Launch targeted marketing campaigns

Increase long-term revenue

The final model predicts:

Churn Probability (0–1 score)

CHURN-FLAG (YES / NO) for high-risk customers

🏢 Business Problem

No-Churn Telecom is facing increasing customer churn due to market competition. Despite promotions and price reductions, the churn rate remains above 10%.

The company wants to:

1️⃣ Identify factors driving customer churn
2️⃣ Predict churn probability using Machine Learning
3️⃣ Flag high-risk customers for retention campaigns

📂 Dataset Information
Attribute	Details
Industry	Telecom
Total Records	4617
Target Variable	Churn (Yes / No)
Data Source	SQL Database
Features	Customer usage, plans, call minutes, customer service calls
🧠 Machine Learning Workflow

The project follows a complete end-to-end ML pipeline.

1️⃣ Data Collection

Telecom customer dataset extracted from SQL database.

2️⃣ Data Preprocessing

Handling missing values

Encoding categorical variables

Feature selection

Removing redundant variables

3️⃣ Exploratory Data Analysis (EDA)

Key insights discovered:

International Plan strongly increases churn risk

Customer Service Calls indicate dissatisfaction

Day Minutes usage correlates with churn

Voicemail Plan reduces churn probability

4️⃣ Handling Imbalanced Data

Used SMOTE (Synthetic Minority Oversampling Technique) to balance churn classes.

5️⃣ Model Training

Algorithms used:

Random Forest Classifier

GridSearchCV for hyperparameter tuning

6️⃣ Model Evaluation

Metrics used:

Accuracy

Precision

Recall

F1 Score

ROC-AUC Score

📈 Model Performance
Metric	Score
Accuracy	91%
ROC-AUC	0.904
Churn Recall	74%

The model successfully identifies 74% of customers likely to churn.

🔑 Key Churn Drivers

Top factors influencing churn:

1️⃣ International Plan
2️⃣ Day Minutes Usage
3️⃣ Customer Service Calls
4️⃣ Voicemail Plan
5️⃣ Evening Minutes Usage

🧾 Final Deliverables

The model generates:

Output	Description
CHURN_RISK_SCORE	Probability of churn (0–1)
CHURN_FLAG	YES / NO prediction
High Risk Customers	Top customers for retention campaigns
🛠 Tech Stack

Programming Language

Python

Libraries Used

Pandas

NumPy

Matplotlib

Seaborn

Scikit-learn

Imbalanced-learn (SMOTE)

PyMySQL

Machine Learning

Random Forest

GridSearchCV

SMOTE

📊 Project Structure
Telecom-Churn-Prediction
│
├── Telecom_ChurnRateMl.ipynb
├── churn_dataset.csv
├── README.md
└── requirements.txt
💻 Installation

Clone the repository:

git clone https://github.com/your-username/telecom-churn-prediction.git

Install dependencies:

pip install -r requirements.txt

Run the notebook:

jupyter notebook
📌 Business Impact

Using this model, telecom companies can:

Identify high-risk customers early

Run targeted retention campaigns

Reduce churn by 30–50%

Improve customer satisfaction

📷 Example Use Case

The system flags customers such as:

Customer ID: 10234
Churn Risk Score: 0.87
CHURN_FLAG: YES

This allows the business to offer discounts, loyalty rewards, or proactive support.

📚 Future Improvements

Possible enhancements:

Deploy model using FastAPI / Flask

Build a customer churn dashboard

Add real-time churn prediction

Train advanced models like XGBoost / LightGBM

👨‍💻 Author

Dhwanit Chokshi

Aspiring AI Engineer & Data Scientist
Skilled in Machine Learning, Generative AI, and Data Analysis
