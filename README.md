# Bank Term Deposit Subscription Prediction

## Project Overview
This project focuses on predicting whether a client will subscribe to a bank term deposit based on direct marketing campaign data. Using a Portuguese banking institution's dataset, we apply several machine learning classifiers to determine which model best identifies potential subscribers, thereby optimizing the bank's marketing efforts and resource allocation.

The project follows the CRISP-DM (Cross-Industry Standard Process for Data Mining) methodology to ensure a structured approach from business understanding to model evaluation.

## Executive Summary
The primary goal is to enhance the efficiency of direct marketing campaigns. By accurately predicting which customers are likely to subscribe to a term deposit, the bank can:

Reduce Operational Costs: Decrease the number of unnecessary phone calls to clients unlikely to convert.

Improve Conversion Rates: Focus human agents and time on "high-quality" leads.

Strategic Scheduling: Identify the best times (such as specific months) to launch campaigns to maximize success.

The project follows the CRISP-DM (Cross-Industry Standard Process for Data Mining) methodology to ensure a structured approach from business understanding to model evaluation.

## Data Overview
The data represents 17 marketing campaigns conducted between May 2008 and November 2010, totaling 79,354 contacts.

Input Features: Includes client demographics (age, job), social-economic indicators, and contact details (duration, month, day of week).

Target Variable: A binary "yes" or "no" indicating if the client subscribed to the term deposit.

### Data Preparation & Modeling Workflow
I utilized a robust Scikit-Learn Pipeline to ensure data integrity and prevent leakage:

* **Cleaning:** Handled missing values via SimpleImputer (Median strategy). To ensure data integrity, the dataset underwent a rigorous cleaning process where I isolated significant variables by removing duplicates and outliers. Our final analysis focused exclusively on vehicles within a price bracket of $500 to $150,000. 

* **Feature Engineering:** Created car_age from year data to better reflect depreciation. 

* **Encoding:** Used TargetEncoder for high-cardinality features (Region/Model) and OneHotEncoder for mechanical specs.

* **Transformation:** Integrated a TransformedTargetRegressor to handle Log-Scale math automatically.

## Critical Depreciation Factors
I have isolated the variables that most significantly reduce a vehicle's market price, providing a baseline for more competitive procurement.
- **Age Impact:** The most critical factor; depreciation follows a non-linear path with the sharpest decline occurring in the initial 3 to 5 years.
- **Mileage Milestones:** While loss of value is constant, a major price drop is observed once a vehicle crosses 100,000 miles.
- **Brand Strength:** High-end brands like Porsche and Lexus retain significantly more value (15–20% higher) than entry-level manufacturers at comparable mileage.


## Model Performance & Reliability
Our **Random Forest** modeling approach proved best for integrated pricing tools, maintaining a stable 70% accuracy with a standard $4,100 margin.
Residual tests show errors are distributed normally, meaning our pricing remains consistent and unbiased across all inventory classes, from budget to luxury.

## Tactical Recommendations for Inventory Tuning
I suggest the following updates to our current buying strategies based on the data:
1. **Target the High-Demand Window:** Focus acquisitions on vehicles that are **4–6 years old** and have **less than 80,000 miles**.
2. **Unified Pricing Systems:** Deploy the **Log-Price Pipeline** to standardize trade-in valuations across all sales locations.
3. **Avoid Regional Mismatches:** Be cautious of low-demand features in specific regions, such as diesel engines in urban centers, to prevent stale inventory.

## Summation and Forward Planning
This model serves as a financial **safeguard**, utilizing a **Log-Transformed** structure to mitigate the risk of price outliers. **Next Phase:** I can proceed with a **"What-If" Scenario** to calculate potential profit gains from further error reduction.

## Setup and Installation

### Project Structure
* `data/vehicles.csv`: The raw dataset containing all car info. **NOTE:** I did not update since the data file is too big and not necessary. 
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
