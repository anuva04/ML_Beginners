# Regression Model Selection
## R Squared
Let's consider a simple linear regression model
- sum of residual of squares, SSres = SUM(Yi - Yi') where Yi = actual data point, Yi' = expected data point
- the regression line is one for which this SSres is minimum
- now if we take an avarage line across all data points (which will obviously be horizontal), then total sum of squares, SStol = SUM(Yi - Yavg) where Yi = actual data point, Yi' = expected data point
- ### R^2 = 1 - (SSres/SStot)
- we want to make SSres as small as possible, which will make R^2 large.
- ideally *SSres = 0* and hence *R^2 = 1*
- R^2 can be negative as well if your model fits the data worse than the average line

## Adjusted R Squared
- by adding more variables to the regression, the SSres will decrease or remain same, but will never increase. Consequently, R^2 will either increase or remain same but will never decrease.
- even for a completely random variable, it will always be true. Hence, we can never know if a variable is actually helping make a better model or not
- hence, we come up with a new Goodness of Fit parameter called Adjusted R Squared
- Adj R^2 = 1 - (1-R^2)(n-1)/(n-p-1); p = number of regressors or independent variables, n = sample size
- How does it help?
  - as number of independent variables increase, (n-p-1) decreases, hence (1-R^2)(n-1)/(n-p-1) increases.
  - again, by adding more variables, R^2 increases and hence (1-R^2)(n-1)/(n-p-1) decreases.
  - so they is tug of war between the 2.
  - if the variable is actually significant, then change in R^2 is more dominating and hence Adj R^2 = 1 - (1-R^2)(n-1)/(n-p-1) increases.
  - however, if the variable is not significant, the change in (n-p-1) is more dominating and hence Adj R^2 = 1 - (1-R^2)(n-1)/(n-p-1) decreases.
***
To find the best model for a dataset, try all models and choose the one with highest R^2 value.\
Following is the code to evaluate model performance using R Squared:
```python
from sklearn.metrics import r2_score
r2_score(y_test, y_pred)
```
