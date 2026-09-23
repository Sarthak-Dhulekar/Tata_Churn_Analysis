### 📊 B2B Telecommunications Customer Risk & Operational Analysis

**Target Company Focus:** Tata Communications / Enterprise Infrastructure
**Author:** Sarthak Dhulekar (AI & Data Science Student) 

### 🏢 1. Executive Problem Statement

Tata Communications is experiencing an annualized customer churn rate of **26.54%**, which significantly exceeds the healthy baseline risk targets for enterprise telecom networks. This represents major recurring revenue leakage. 

* **Primary Objective:** Uncover the root operational causes behind customer churn and provide data-backed strategic recommendations to the executive board to secure long-term revenue retention.

### 🛠️ 2. Data Pipeline & Quality Assurance (Data Cleaning)

The raw dataset was sourced from Kaggle to inspect features, structural integrity, and hidden anomalies using Python (pandas): 

* **Data Type Rectification:** The TotalCharges column was incorrectly imported as an object/string type. This occurred because of hidden blank space strings (" ") embedded in the data. The column was successfully vectorized into a numeric type (float64) using pd.to_numeric().
* **Missing Value Strategy:** While a standard .isnull().sum() check initially showed zero null values, converting TotalCharges exposed the hidden blank spaces as NaN values. These records perfectly mapped to customers with a tenure of 0 months. They were logically imputed with a value of 0 using .fillna(0).
* **Structural Integrity:** Validated the unique constraint of the dataset using df['customerID'].duplicated().sum(). The output returned 0, confirming that no duplicate client entries or double-counted rows exist in the pipeline.

### 🔎 3. Core Analytical Findings & Insights (The Evidence)

Through systematic cross-tabulation and behavioral profiling, the core drivers of revenue risk were successfully isolated: 

* **🚨 Finding 1: The 10-Month Customer Danger Zone** 

  * **The Evidence:** Loyal, active customers exhibit a high median tenure of **38 months**. Conversely, churned customers drop out of the system at a sharp median threshold of **10 months**.
  * **The Business Story:** Half of all client attrition happens in a customer's very first year, highlighting a critical failure point during early account onboarding.
* **📉 Finding 2: Month-to-Month Contract Vulnerability** 

  * **The Evidence:** Breaking down churn across contractual agreements revealed: 

    * **Month-to-Month:** 2,220 Stayed | 1,655 Churned (~42.7% Churn Rate)
    * **One Year:** 1,307 Stayed | 166 Churned (~11.2% Churn Rate)
    * **Two Year:** 1,647 Stayed | 48 Churned (~2.8% Churn Rate)
  * **The Business Story:** Month-to-month flexibility is the single largest risk catalyst, accounting for over **88%** of the company's total customer losses. Long-term contract locks almost entirely freeze churn.
* **✅ Finding 3: The Fiber Optic & Security Infrastructure Crisis** 

  * **The Evidence:** Isolating the core utility products revealed a major product failure: 

    * Standard DSL users are highly stable, with a low churn rate of **18.9%**.
    * High-speed Fiber Optic users exhibit an alarming churn rate of **41.89%**.
    * When cross-referenced with add-on options, Fiber Optic users **WITHOUT** OnlineSecurity experience a devastating **49.3%** churn rate. However, when OnlineSecurity is active, Fiber Optic churn plummets down to **21.8%**.
  * **The Business Story:** High-speed Fiber Optic is our most popular product but it causes frustration and massive churn due to digital instability. Activating security safeguards drops customer defections by more than half.

### 💡 4. Data-Driven Strategic Recommendations (The Action)

Based on the empirical evidence uncovered in this analysis, I propose three immediate strategic changes for the operational directors: 

1. **Mandatory Product Bundling:** Because the data proves that un-protected high-speed lines suffer a near 50% churn rate, Tata should completely eliminate standalone Fiber Optic sales. Automatically bundle OnlineSecurity into the core subscription as a baseline requirement.
2. **Contract Migration Campaign:** To mitigate the extreme volatility of Month-to-Month accounts, the marketing team should launch an automated promotional discount offer targeted directly at users as they hit their 6th month of tenure, actively driving them into 1-year or 2-year locked agreements before they hit the 10-month "Danger Zone."
3. **Proactive CRM Alerts:** Build an automated trigger flag within the account management platform. If a customer is on a Month-to-Month contract using un-secured Fiber Optic lines, they should be flagged as "High Attrition Risk" for priority check-ins by customer success managers.
