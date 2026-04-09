# Bank Term Deposit Subscription Prediction

## Project Overview
The objective of this project is to improve the efficiency and effectiveness of a bank's direct marketing campaigns by building a predictive model. The campaigns ran between May 2008 and November 2010, involving 79,354 contacts to promote a long-term deposit application with attractive interest rates. The primary channel for contact was telephone.

The project follows the CRISP-DM (Cross-Industry Standard Process for Data Mining) methodology to ensure a structured approach from business understanding to model evaluation.

## Executive Summary
The primary goal is to enhance the efficiency of direct marketing campaigns. By accurately predicting which customers are likely to subscribe to a term deposit, the bank can:

- **Reduce Operational Costs:** Decrease the number of unnecessary phone calls to clients unlikely to convert.

- **Improve Conversion Rates:** Focus human agents and time on "high-quality" leads.

- **Strategic Scheduling:** Identify the best times (such as specific months) to launch campaigns to maximize success.

The project follows the CRISP-DM (Cross-Industry Standard Process for Data Mining) methodology to ensure a structured approach from business understanding to model evaluation.

## Data Overview
The data represents 17 marketing campaigns conducted between May 2008 and November 2010, totaling 79,354 contacts.

- **Input Features:** Includes client demographics (age, job), social-economic indicators, and contact details (duration, month, day of week). Only bank attributes are used as requested.

- **Target Variable:** A binary "yes" or "no" indicating if the client subscribed to the term deposit.

## Data Preparation
- **Handling Categorical Variables:** The notebook uses One-Hot Encoding (via pd.get_dummies) to convert categorical features (like job, marital, and education) into binary (0 or 1) columns. This prevents the models from assuming a mathematical ranking between categories (e.g., assuming "Technician" is "greater" than "Admin").

- **Correlation Analysis:** The notebook performs a correlation check (often visualized via a heatmap) to identify variables that move in perfect or near-perfect lockstep. Redundancy in this dataset often comes from Multicollinearity, where two or more features provide the exact same information. High redundancy can confuse models and increase training time unnecessarily. The dataset contains several closely related economic features: emp.var.rate (employment variation rate), cons.price.idx (consumer price index), cons.conf.idx (consumer confidence index), euribor3m (3-month interest rate), and nr.employed (number of employees). Because these features are often highly correlated (e.g., as employment rates change, interest rates often follow), the analysis identifies that keeping all of them may be redundant.

- **The "Unknown" Filter:** While not strictly redundant, the notebook treats the 'unknown' string values as a specific category. In some iterations of data cleaning, rows with too many "unknowns" may be dropped or consolidated to reduce noise in the data.

- **Target Variable Encoding:** The target column y (the subscription outcome) is mapped from 'yes'/'no' to 1/0.

- **Feature Scaling:** Because models like KNN and SVM rely on calculating distances between data points, the notebook applies StandardScaler. This scales numerical features (like age or duration) to have a mean of 0 and a standard deviation of 1, ensuring that features with large numerical ranges do not dominate the model. By combining One-Hot Encoding with Correlation Filtering, the notebook transforms a messy, text-heavy dataset into a streamlined numerical matrix optimized for high-performance classification.

- **Train-Test Split:** The data is typically split (often 70/30 or 80/20) into a training set to build the models and a testing set to evaluate how they perform on unseen data.

## Modeling Workflow
Hyperparameter tuning using search algorithms (e.g., grid search) on existing models (e.g., tuning the number of neighbors in KNN or maximum depth of a Decision Tree).

## Model Performance & Reliability

The Logistic Regression model, especially after balancing with SMOTETomek, consistently demonstrated the best balance of recall for class 1 and acceptable overall performance. Its Recall of 0.615 means it correctly identified over 61% of the actual subscribers, a crucial improvement for the business objective. While the initial SVC with balanced data had a very high recall, its extremely low precision and accuracy made it impractical. The tuned SVC improved slightly but still lagged behind Logistic Regression in overall utility.

## Recommendations

Based on SHAP interpretability and model performance metrics, the bank should prioritize age-based segmentation and cellular contact methods for its marketing campaigns. Analysis of monthly variations in subscriptions and specific demographics like administrative professionals can further optimize scheduling and messaging. By focusing on recall over accuracy through techniques like SMOTETomek, the model better identifies potential subscribers, though continuous monitoring and periodic retraining are necessary to maintain relevance amid changing market conditions.

## Conclusion

This analysis established a robust machine learning pipeline to predict term deposit subscriptions. By utilizing SMOTETomek and recall-focused hyperparameter tuning, I developed models that outperfromed simple baselines in identifying potential customers. 
SHAP analysis revealed 'age' and 'contact_cellular' as primary predictive drivers. 

These insights enable the bank to refine marketing strategies, optimize resource allocation, and improve acquisition rates for new term deposit clients.

## Setup and Installation

### Project Structure
* `prompt_III.ipynb`: A comprehensive Jupyter Notebook containing data cleaning, exploratory data analysis (EDA), feature engineering, and modeling.

### Prerequisites
You will need Python 3.x and the following libraries:
* `pandas`
* `seaborn`
* `matplotlib`
* `plotly`
* `sklearn`

### Running the Analysis
1. Clone the repository:
   `git clone https://github.com/tnralakus/subscription_prediction.git`
2. Navigate to the directory and launch Jupyter:
   `jupyter notebook prompt_III.ipynb`
