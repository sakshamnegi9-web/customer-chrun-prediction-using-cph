<div align="center">
  <h1> Telco Churn: Survival & Strategic Retention</h1>
  <p><i>Using Cox Proportional Hazards to predict Customer "Life Expectancy"</i></p>
  <hr />
</div>

<h2> Project Objective</h2>
<p>
  Traditional churn models focus on <b>IF</b> a customer leaves. As an MBA student, I wanted to focus on <b>WHEN</b>. 
  By implementing <b>Survival Analysis (CPH)</b>, this project identifies the specific milestones where 
  customer risk peaks, allowing for a data-driven retention schedule rather than a reactive one.
</p>

<h2> Why Survival Analysis?</h2>
<p>
  During the EDA, it became clear that churn is not a static event—it is a race against time. 
  I chose the <code>lifelines</code> library because it handles <b>Censored Data</b>—customers who 
  are still active but may churn tomorrow—more accurately than standard Logistic Regression.
</p>

<div style="background-color: #f9f9f9; padding: 15px; border-left: 5px solid #2196F3;">
  <h3> The Recursive Milestone Logic</h3>
  <p>
    I developed a <b>Recursive Survival Chain</b> to track how risk "resets." If a customer survives 
    their first 12 months, their 50% risk milestone shifts. This code visualizes those 
    shifting horizons to help marketing teams understand the evolving customer lifecycle.
  </p>
</div>

<h2>The "Borrowed Time" Metric</h2>
<p>
  The core output of this script is the <b>Remaining Tenure</b> column:
</p>
<ul>
  <li><b>Positive Value:</b> The customer is statistically in a "Loyalty Zone."</li>
  <li><b>Negative Value:</b> The customer is on <b>"Borrowed Time."</b> They have survived past their 
  predicted 50% risk month. These are the <b>#1 Priority</b> for retention interventions.</li>
</ul>

<h2> Technical Workflow</h2>
<table>
  <tr>
    <th>Phase</th>
    <th>Description</th>
  </tr>
  <tr>
    <td><b>Data Cleaning</b></td>
    <td>Handled <code>TotalCharges</code> formatting errors and handled nulls for model stability.</td>
  </tr>
  <tr>
    <td><b>EDA</b></td>
    <td>Visualized Churn Density vs. Tenure to identify "Danger Zones" (first 18 months).</td>
  </tr>
  <tr>
    <td><b>Modeling</b></td>
    <td>Trained a <b>Cox Proportional Hazards</b> model focusing on Contract types and Monthly Charges.</td>
  </tr>
  <tr>
    <td><b>Reporting</b></td>
    <td>Created a priority dashboard showing the <b>Most At-Risk Customers</b>.</td>
  </tr>
</table>

<h2> Setup & Usage</h2>
<pre>
1. Place 'WA_Fn-UseC_-Telco-Customer-Churn.csv' in the folder.
2. Install: pip install pandas lifelines seaborn matplotlib
3. Run: python churn_survival_model.py
</pre>

<hr />
<div align="center">
  <sub>Developed by <b>Saksham</b> | MBA Analytics & Data Science</sub>
</div>
