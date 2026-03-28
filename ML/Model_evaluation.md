
# Model Training & Evaluation

## Objective
The objective of the model is to **predict the probability of an SLA breach at the ticket level**, enabling proactive risk identification and operational prioritization.

A binary classification approach is used with Logistic Regression as the baseline model.

---

## Model Choice

**Logistic Regression** was selected because:
- It provides probabilistic outputs suitable for risk scoring
- It is interpretable and stable for operational use cases
- It integrates well with Spark ML pipelines

Regularization is applied (`regParam = 0.01`) to prevent overfitting.

---

## Feature Processing Pipeline

A Spark ML Pipeline is used to ensure reproducibility and consistency across training and scoring.

Pipeline stages include:
1. **StringIndexer**
   - Converts categorical variables into indexed numeric form
   - Handles unseen categories using `handleInvalid="keep"`
2. **OneHotEncoder**
   - Encodes indexed categorical variables into sparse vectors
3. **VectorAssembler**
   - Combines encoded categorical and numeric features
4. **StandardScaler**
   - Standardizes features (mean = 0, variance = 1)
5. **Logistic Regression**
   - Produces ticket-level breach probabilities

---

## Train-Test Split

Data is split into:
- **80% Training set**
- **20% Test set**

A fixed random seed ensures reproducibility.

---

## Evaluation Metric

The model is evaluated using:

- **Area Under the ROC Curve (AUC)**

AUC was chosen because:
- The dataset is imbalanced (fewer breached tickets)
- AUC measures the model’s ability to rank risky tickets correctly
- It is more informative than accuracy for risk prediction tasks

The test AUC is printed after model training to validate discriminatory power.

---

## Model Persistence

After training, the full pipeline model is saved to OneLake using the ABFS path:

- Stored under `/Files/models/breach_lr_model`
- Enables reuse for scoring without retraining
- Supports production-style deployment patterns

---

## Scoring & Output

The trained model is applied to all feature rows to produce:

- `BreachRisk` – probability that a ticket will breach SLA

The probability is extracted from the positive class output of the Logistic Regression model and written to a Gold-layer Delta table:

- `gold_fact_ticket_scored`

This table is used directly by Power BI for:
- ML & Risk Insights dashboard
- Tail-risk (P90/P95) analysis
- High-risk ticket identification

---

## Design Considerations

- Probabilistic outputs allow flexible thresholding
- Percentile-based metrics are preferred over averages due to skewed risk distributions
- Pipeline-based approach ensures consistent transformations during training and inference

---

## Implementation Reference

📓 **Training and scoring implementation:**  
[/Breach_model.ipynb]([/Breach_model.ipynb)
