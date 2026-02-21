
# Understanding Skewness in Financial Data

## What is Skewness?

Skewness measures the asymmetry of a feature’s distribution.

In financial datasets, many variables are naturally skewed:
- Income
- Loan Amount
- Transaction Amount
- Credit Exposure

Most values are small/moderate, while a few are extremely large.
This creates a right-skewed distribution.

---

## Why Financial Data is Skewed

Financial systems naturally produce skewed distributions because:

- Income is unevenly distributed
- Loan sizes vary widely
- Transactions follow heavy-tailed behavior
- Credit exposure is concentrated among fewer entities

This is normal in real-world banking data.

---

## Impact on Machine Learning Models

### Linear Models
Skewed features can:
- Distort coefficients
- Increase variance
- Reduce model stability

Log transformation is often necessary:

```python
import numpy as np
df['log_income'] = np.log1p(df['person_income'])
