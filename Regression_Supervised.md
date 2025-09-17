# Regression

<div class="phase-title">Phase 1: Problem Definition and Data Collection</div>
<table class="clean">
  <tr><th>Step</th><th>Action</th><th>Notes</th></tr>
  <tr><td>1</td><td>Define Business Objectives</td><td>Clarify the problem, project goals, Key Performance Indicators (KPIs), and success criteria.</td></tr>
  <tr><td>2</td><td>Define Data Strategy</td><td>Identify and gather data from sources like APIs, databases, or public datasets.</td></tr>
</table>

<div class="phase-title">Phase 2: Ingestion & Assessment </div>
<table class="clean">
  <tr><th>Step</th><th>Action</th><th>Notes</th></tr>
  <tr><td>3</td><td>Initial File Verification</td>
      <td>Check if the dataset files exist, are accessible, and in the correct format (e.g., CSV, Excel). Confirm correct encoding and delimiter.</td></tr>
  <tr><td>4</td><td>Module and Data Load</td>
      <td>Import necessary libraries (e.g., pandas, numpy) and load the data into memory for exploration.</td></tr>
  <tr><td>3</td><td>Initial Exploration and Assessment</td>
      <td>Use methods like <code>df.info()</code>, <code>df.describe()</code>, and <code>df.head()</code> to assess structure, data types, and basic statistics.</td></tr>
</table>

<div class="phase-title">Phase 3: Initial Cleaning </div>
<table class="clean">
  <tr><th>Step</th><th>Action</th><th>Notes</th></tr>
  <tr><td>3</td><td>Handling Duplicates</td>
      <td>Identify and remove duplicate rows using <code>df.duplicated()</code> and <code>df.drop_duplicates()</code> to ensure data integrity.</td></tr>
  <tr><td>4</td><td>Inconsistent Formatting</td>
      <td>Detect and fix formatting issues like inconsistent casing, extra spaces, or mixed data types in categorical fields.</td></tr>
  <tr><td>5</td><td>Data Corruption or Abnormal Values</td>
      <td>Look for corrupted, nonsensical, or extreme outlier values that may indicate data entry issues or sensor errors. Use domain knowledge or statistical thresholds to flag and address them.</td></tr>
</table>
     
<div class="phase-title">Phase 4: Exploratory Data Analysis (EDA) </div>
<table class="clean">
  <tr><th>Step</th><th>Action</th><th>Notes</th></tr>
  <tr><td>5</td><td>Initial EDA</td><td>Plot histograms, boxplots, and use summary stats. Use scatterplots and correlation matrices to identify relationships.</td></tr>
  <tr><td>6</td><td>Analyze Target Variable</td><td>Examine the distribution of the target variable (<code>y</code>). Check for class imbalance, skew, and outliers.</td></tr>
  <tr><td>7</td><td>Identify Potential Outliers</td><td>Use visualizations (histograms, boxplots) and statistical methods (Z-scores, Isolation Forest) to detect potential outliers. Do not remove or modify them yet.</td></tr>
</table>
     
<div class="phase-title">Phase 5: Data Splitting</div>
<table class="clean">
  <tr><th>Step</th><th>Action</th><th>Notes</th></tr>
  <tr><td>8</td><td>Split Data</td><td>Divide the dataset into training, validation, and test sets. A common split is 80%/10%/10%.</td></tr>
  <tr><td>9</td><td>Save the Test Set</td><td>Store the test set separately and do not use it for any purpose until the final model evaluation to prevent data leakage.</td></tr>
</table>

<div class="phase-title">Phase 6: Preprocessing (Train/Validation Data Only)</div>
<table class="clean">
  <tr><th>Step</th><th>Action</th><th>Notes</th></tr>
  <tr><td>10a</td><td>Handle Outliers</td><td>On training data only: Remove outliers using methods like IQR or Z-score. Transform skewed data using log, square root, or Box-Cox transformations.</td></tr>
  <tr><td>10b</td><td>Handle Missing Values</td><td>Impute missing values using techniques like mean/median for numerical data or mode for categorical data.</td></tr>
  <tr><td>10c</td><td>Encode Categorical Variables</td><td>Apply one-hot encoding for nominal features, label encoding for ordinal features, and other techniques for high-cardinality features.</td></tr>
  <tr><td>10d</td><td>Process Text Features</td><td>Clean, tokenize, and vectorize text using methods like TF-IDF or word embeddings.</td></tr>
  <tr><td>10e</td><td>Feature Scaling</td><td>Fit the scaler on the training data only, then transform both the training and validation sets using methods like StandardScaler or MinMaxScaler.</td></tr>
</table>

<div class="phase-title">Phase 7: Feature Engineering</div>
<table class="clean">
  <tr><th>Step</th><th>Action</th><th>Notes</th></tr>
  <tr><td>11</td><td>Create New Features</td><td>Derive new features (e.g., polynomial, interaction) from existing ones.</td></tr>
</table>

<div class="phase-title">Phase 8: Feature Selection and Dimensionality Reduction</div>
<table class="clean">
  <tr><th>Step</th><th>Action</th><th>Notes</th></tr>
  <tr><td>12</td><td>Feature Selection</td><td>Select the most relevant features using techniques like Lasso regularization, Recursive Feature Elimination (RFE), or feature importance scores.</td></tr>
  <tr><td>13</td><td>Dimensionality Reduction</td><td>Apply PCA, t-SNE, or other techniques if needed to reduce feature space for high-dimensional data.</td></tr>
</table>

<div class="phase-title">Phase 9: Modeling and Evaluation (Train/Validation Data Only)</div>
<table class="clean">
  <tr><th>Step</th><th>Action</th><th>Notes</th></tr>
  <tr><td>14</td><td>Modeling</td><td>Train multiple candidate models on the prepared training data.</td></tr>
  <tr><td>15</td><td>Cross-Validation</td><td>Use K-Fold cross-validation on the training data to get a robust estimate of model performance.</td></tr>
  <tr><td>16</td><td>Hyperparameter Tuning</td><td>Use techniques like GridSearchCV or RandomizedSearchCV to optimize model hyperparameters within the training data.</td></tr>
  <tr><td>17</td><td>Validation Evaluation</td><td>Evaluate the tuned models on the validation set using chosen metrics (e.g., RMSE, MAE, R²).</td></tr>
</table>

<div class="phase-title">Phase 10: Final Evaluation and Deployment</div>
<table class="clean">
  <tr><th>Step</th><th>Action</th><th>Notes</th></tr>
  <tr><td>18</td><td>Final Prediction</td><td>Apply the entire trained pipeline to the completely unseen test set. Never refit or reprocess the test data.</td></tr>
  <tr><td>19</td><td>Final Evaluation</td><td>Evaluate the final model on the test set using the same metrics. Report performance.</td></tr>
  <tr><td>20</td><td>Interpretation</td><td>Explain model predictions using tools like SHAP or feature importance plots.</td></tr>
  <tr><td>21</td><td>Deployment Preparation</td><td>Save the final model and the complete preprocessing pipeline.</td></tr>
  <tr><td>22</td><td>Monitoring</td><td>Plan for monitoring the model's performance and data/concept drift in production. Define retraining triggers.</td></tr>
</table>
