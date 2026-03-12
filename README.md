Telco Churn: Survival Analysis for Retention Strategy
By Saksham

The Objective
Most churn projects only predict if a customer will leave. For my MBA portfolio, I wanted to go deeper. Using Cox Proportional Hazards (CPH), I built a model that predicts when a customer is likely to reach a 50% churn risk threshold. This allows a marketing team to stop guessing and start timing their interventions.

Why Survival Analysis?
During my initial EDA, I noticed that churn isn't random; it’s heavily tied to the "Contract Lifecycle."

Month-to-month users are high-risk early on.

Two-year contract holders have a "grace period" but become high-risk as the contract nears expiration.

Traditional classification (like Random Forest) misses this "time" element. I chose the lifelines library to model the actual tenure velocity of the customers.

The "Recursive Milestone" Logic
One unique part of this code is the Recursive Survival Chain.
Risk isn't a one-time calculation. If a customer survives the first 12 months, their risk profile resets. I wrote a recursive loop to track how that "Median Risk Month" shifts as a customer stays loyal.

Key Feature: The "Remaining Tenure" Metric
In the final report, you’ll see some negative values.

Positive value: The customer is still in the "safe" zone.

Negative value: This is what I call "Borrowed Time." These customers have already passed the month where 50% of their peers usually churn. They are statistically overdue to leave and should be the #1 priority for the sales team.

Technical Workflow
Cleaning: Handled TotalCharges inconsistencies (converting strings to floats) and managed missing values to ensure model stability.

EDA: Visualized churn density using KDE plots to identify the "Danger Zones" in the customer lifecycle.

Modeling: Implemented a semi-parametric Cox PH model, selecting features like MonthlyCharges and Contract which showed the highest correlation with attrition.

Reporting: Structured the output to show Actual Status vs. Predicted Milestone, making it readable for non-technical stakeholders.

How to Run
Ensure you have the Telco dataset (WA_Fn-UseC_-Telco-Customer-Churn.csv) in the root directory.

Install dependencies: pip install pandas lifelines seaborn matplotlib

Run the script to generate the EDA plots and the Urgent Retention Priority List.

Making it your own:
The "I" Factor: Notice I used "I noticed," "I wanted," and "I wrote." This makes it clear these were your decisions.

Business Language: Using terms like "Interventions," "Stakeholders," and "Retention Strategy" highlights your MBA background.

Self-Correction: Mentioning the TotalCharges strings shows you actually spent time cleaning the data, which is a very "human" part of the process.
