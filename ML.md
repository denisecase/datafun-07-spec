# Option 1. Applied Data Analytics: ML

Basic Machine Learning (ML): 
Explore fundamental ML concepts using Python's statistical and visualization libraries with simple linear regression and predictive analytics.

Here's the missing part of the general specification. This goes after the logging section.
Renumber the sections to be consistent with the outline in the general specification.

## Module Specification

### Requirements

#### 5. Data Acquisition

Load the Seaborn tips dataset like we did the iris dataset.

```python
import seaborn as sns
import pandas as pd

# Load data into DataFrame
df = sns.load_dataset('tips')

```

#### 6. Basic Data Exploration

First, use pandas to perform the basic data exploration tasks as the initial steps of
any data analysis project:

1. Load Data into DataFrame
2. Inspect Data w/head(), shape, and dtypes
3. Describe Summary Statistics
4. Display Histograms for Numeric Columns

For example:

```python
import pandas as pd
import matplotlib.pyplot as plt

# earlier loading.... 

# Inspect data with head(), shape, and dtypes
print(df.head(10))
print(df.shape)
print(df.dtypes)

# Describe summary statistics
print(df.describe())

# Display histograms for numeric columns
df.hist(figsize=(10, 8))
plt.show()
```

#### 7. Data Visualization

Create a scatter chart of total bill amount vs tip amount.
For example:
  
```python
# Create scatter chart of total bill amount vs tip amount
sns.scatterplot(x='total_bill', y='tip', data=df)
plt.xlabel('Total Bill')
plt.ylabel('Tip')
plt.title('Tip vs Total Bill')
plt.show()
```

#### 9. Model Building

Build a simple linear regression model to predict tip amount based on total bill amount.

Use the SciPy stats module linregress function to calculate slope and intercept for the best fit line through the data.

Redraw the scatter chart with the best fit line. 

Use the line equation (model) to predict tip amount for a total bill amount of $50.00.

Draw this point on the chart. 

For example:

```python
import seaborn as sns
import pandas as pd
import matplotlib.pyplot as plt
from scipy import stats

# ... initial EDA ....

# ... initial scatter chart... 

# Build a simple linear regression model to 
# predict tip amount based on total bill amount
# lingress() returns a tuple that includes the 
# slope and intercept for the best fit line
# as well as other statistical measures
slope, intercept, r_value, p_value, std_err = stats.linregress(df['total_bill'], df['tip'])

# Display the results of the model
print(f"Slope: {slope}")
print(f"Intercept: {intercept}")
print(f"R-squared: {r_value**2}")
print(f"P-value: {p_value}")
print(f"Standard Error: {std_err}")

# Discuss the results - is this a good model?
# How do you know? Use numbers, be specific. 

# Redraw the scatter chart with the best fit line
sns.scatterplot(x='total_bill', y='tip', data=df)

# Use the line equation (model) to predict tip amount 
# for a total bill amount of $50.00
x = 50
y = slope * x + intercept

# Draw this point on the chart
plt.scatter(x, y, color='red')
plt.show()


# Discuss the results - is this a good prediction?
# How do you know? Why or why not? Use numbers, be specific. 
```

#### 10. Storytelling and Presentation

Interpret the process and results to craft a narrative around your findings.
Add additional visualizations around the independent (bill amount) and dependent variable (tip amount).
Consider questions such as:

- "Does the model have any limitations?"
- "How could the model be improved?"
- "Are there any potential biases or factors not accounted for in the model?"

Present your findings in a logical and engaging manner.

## Model Validation

The following metrics are used to evaluate the performance of a linear regression model.

R-squared (Coefficient of Determination)

This statistic provides an indication of the goodness of fit of a set of predictions to the actual values.
In simple terms, it represents how well the independent variable (total bill) explains the variability in the dependent variable (tip).
An R-squared value closer to 1 indicates a model that explains a large portion of the variance in the dependent variable.

P-value

This value helps you determine the statistical significance of your model coefficients. A low p-value (typically ≤ 0.05) indicates that you can reject the null hypothesis, which states that the coefficient is equal to zero (no effect).

Standard Error

This statistic measures the average amount that the estimated coefficients differ from the actual average value of our response variable. A lower standard error of the coefficient suggests more precise estimates.

```python
print(f"R-squared: {r_value**2}")
print(f"P-value: {p_value}")
print(f"Standard Error: {std_err}")
```
