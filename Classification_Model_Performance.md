# False Positives and False Negatives
- false positive means it was predicted that a certain event would occur but in reality it did not occur (less dangerous/ type 1 error)
- false negative means it was predicted that a certain event would not occur but in reality it did occur (more dangerous/ type 2 error)
- both can be pretty serious if we are dealing with sensitive issues like medical information

# Confusion Matrix
- confusion matrix is a 2x2 matrix
- m[1][1]: event is predicted to occur and it actually occurs (true positive)
- m[0][0]: event is predicted to not to occur and it actually doesn't occur (true negative)
- m[0][1]: event is predicted to occur but it actually doesn't occur (false positive)
- m[1][0]: event is predicted not to occur but it actually occurs (false negative)
- accuracy rate = correct/total
- error rate = wrong/total

# Accuracy Paradox
- if anyone of the cells in the confusion matrix has a large value compared to others, it will dominate the accuracy rate
> for example: <br>
> m[0][0]=9700, m[0][1]=150, m[1][0]=50, m[1][1]=100 <br>
> here, accuracy rate = 9800/10000 = 98% <br>
> now, if we abandon this model and say for every datapoint, we will predict it as 0, then <br>
> m[0][0]=9850, m[0][1]=0, m[1][0]=150, m[1][1]=0 <br>
> here, accuracy rate = 9850/10000 = 98.5% which is higher than previous rate <br>
- hence accuracy rate cannot be used in every situation

# Cummulative accuracy profile (CAP)
- suppose we have a dataset where y is linearly proportional to x
- if we use a ML model to predict the number of datapoints which have higher chances of occuring and operate on them first before operating on less likely data points, we can get better results than the linear model
- this is called CAP
- the area between the new curve and the orginal linear curve determines the efficiency of the ML model being used. More the area, better the model
- **Cummulative Accuracy Profile != Receiver Operating Characteristic**
# Analysing CAP curve
- the linear curve is called random model
- a model in which all the correct predictions are operated on first is called a perfect model
- for any particular model, the ratio of the area between this model and the random model with the area between this model and the perfect model is the accuracy measure
- this value is between 0 and 1; the closer it is to 1, the more efficient the model is
- calculating area can be quite difficult, hence an alternative method is used
- take the 50% mark on the horizontal line and project it on the vertical line through your model
- if it is less than 60%, model is not good
- if it is less than 70%, it is still poor
- if it is 70-80% it is good
- 80-90% is very good
- greater than 90% is too good (chances of overfitting)
