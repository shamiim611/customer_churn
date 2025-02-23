# customer_churn Analysis
## Data Dictionary
The dataset includes the following information:
- **Churn**: Indicates whether a customer left within the last month.
- **Services**: Details on customer subscriptions, including:
  - Phone,Multiple lines,Internet (fiber optic, DSL, or none)
  - Online security,Online backup,Device protection,Tech support
  - Streaming TV & movies
- **Customer Account Information**:
  - Tenure (how long the customer has been subscribed)
  - Contract type (month-to-month, one-year, two-year)
  - Payment method,Paperless billing status
  - Monthly charges,Total charges
- **Demographics**:
  - Gender,Age range
  - Whether the customer has a partner,Whether the customer has dependents

## Insights from Odds Ratio Plot
### Key Findings to Reduce Churn:
- Customers with **month-to-month contracts** and **fiber optic internet** are at the highest risk of churning.
- **Longer contract commitments** (e.g., two-year contracts) are associated with lower churn rates.
- Customers who use **automatic payments** are less likely to churn.

### Recommended Actions:
- Improve customer experience for month-to-month subscribers.
- Offer retention incentives for fiber optic customers.
- Encourage customers to switch to longer-term contracts.
- Promote automatic payment options to improve retention.

## Confusion Matrix Interpretation
- **Precision: 63%** – Out of all predicted churners, 63% actually churned.
- **Recall: 52%** – The model correctly identified 52% of actual churners.
- **F1 Score: 57%** – A balanced measure of precision and recall, indicating moderate model performance.
- The model performs better on the majority class (non-churners), but it misses a significant portion of actual churners (false negatives).

## Model Comparison
### Logistic Regression:
- **Strengths:** High accuracy for non-churners.
- **Weaknesses:** Low recall for churners, missing many actual churners.

### Decision Tree:
- **Strengths:** Higher recall for churners (identifies more true churners).
- **Weaknesses:** Lower overall accuracy and more false positives.

### Random Forest (Best Performing Model):
- **Improvements:**
  - Used `class_weight='balanced'` to handle class imbalance.
  - Lowered decision threshold to 0.4.
  - Removed unnecessary features and retrained for better performance.

## Recommendations
- **If identifying as many churners as possible is the goal:** Use **Decision Tree** due to its higher recall.
- **If minimizing false positives is more important:** Use **Logistic Regression** for better precision.
- **Further Improvements:**
  - Address class imbalance with **SMOTE, class weighting, or oversampling**.
  - **Hyperparameter tuning** for improved performance:
    - Adjust decision threshold for Logistic Regression.
    - Tune max depth, min samples split, and min samples leaf for Decision Tree.
  - Consider **ensemble models** like **Random Forest** or **Gradient Boosted Trees** to combine strengths of both models.
  - Further refine **feature selection** to improve model efficiency.
