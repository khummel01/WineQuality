# Predicting Wine Quality of Red Variants of the Portuguese “Vinho Verde” Wine

[Data set taken from Kaggle] (https://www.kaggle.com/uciml/red-wine-quality-cortez-et-al-2009 )

## Abstract

This report examines 1,599 red variants of the Portuguese “Vinho Verde” wine using linear regression methods. The primary goal is to determine what predictor variables are most effective at predicting the quality of wine, as well as to see if there is a certain combination of predictor variables that most accurately predicts the quality of wine. Wine quality was reported as a sensory value judgement on a scale from 0 to 10 (10 being the best wine). The eleven predictor variables were fixed acidity, volatile acidity, citric acid, residual sugar, chlorides, free sulfur dioxide, total sulfur dioxide, density, pH, sulphates, and alcohol. Unfortunately, the data set did not specify the units on any of the predictor variables. 

## Results

**Final model output**

`Residual standard error: 0.6345 on 1588 degrees of freedom`\
`Multiple R-squared:  0.3865,	Adjusted R-squared:  0.3826`\
`F-statistic:   100 on 10 and 1588 DF,  p-value: < 2.2e-16`

The adjusted R^2 for this model is 0.3826. This is an improvement from our full-order model, manual backward elimination, and manual backward elimination with added interaction effects where R^2 was 0.354, 0.354, and 0.381 respectively, accounting for a greatest difference of 0.028. Furthermore, the residual standard error of this model is  0.6345, a decrease by a factor of 0.015, 0.015, and 0.000429 from the full-order, reduced, and reduced model with added interaction effects respectively. 

**Residuals**

![alt text] (https://github.com/khummel01/WineQuality/tree/master/images/residuals.png "Residuals")

The plot of residuals vs fitted values shows no major departures from the assumptions of constant variance, absence of outliers, and lack of curvature. The normal Q-Q plot shows that the data do not appear to be non-normal, except for a slight left skew. The Scale-Location plot indicates very non-constant variance. Because this plot indicates such strongly different conclusions from the other plots, we believe that the crook in the LOWESS line on the Scale-Location plot is due to the quasi-continuity of our response variable. There are no points with a leverage above the leverage cutoff, 25.3, and the Cook's distance cutoff is so far beyond the range of the data that it is not on the plot, so we are not concerned that any particular data point has too great an effect on the model. 

The studentized deleted residuals shows two points of concern. The have studentized deleted residuals with an absolute value greater than 4. This indicates that they might be outliers. 

## Conclusion

We have found that for red variants of the Portuguese “Vinho Verde” wine:

1.	Alcohol was the only predictor variable with a fair correlation with wine quality (r = 0.48). 
2.	The pairs and correlation plots indicated a strong negative linear relationship between fixed acidity and pH (r= -0.69). 
3.	There were mild negative linear relationships between volatile acidity and citric acid (r = -0.54), pH and citric acid (r = -0.55), and alcohol and density (r = -0.53). 
4.	Only one strong positive linear relationship exists between fixed acidity and density (r = 0.63). Strong, but non-linear correlations were found between free sulfur dioxide and total sulfur dioxide (r=0.68) and fixed acidity and citric acid (r = 0.68).
5.	We concluded that there was no statistically significant difference between the transformed residual sugars and chlorides and the untransformed residual sugars and chlorides. The distributions of the predictor variable became more evenly distributed, but not more linear. 
6.	The final model explained 38.3% of the variation in wine quality.
7.	Prediction intervals of wine quality had margins of error equal to about +/- 1.25 quality units and 24% of the predicted values.
8.  Three interaction effects are significant. The most significant interaction effect is volatile_acidity x total sulfur dioxide to a false-positive rate of α = .001. Total sulfur dioxide x sulphates and sulphates x alcohol are also significant interactions to a false-positive rate of α = .005.


In summation, there is no single predictor that precisely predicts the quality of red wine by itself; rather by combining many together with included interaction effects results in more accurately predicted red wine quality levels. We achieved a R^2 value of 0.383 in our final model using ten predictors including interaction effects with a residual standard error of 0.63.

Our dataset does not allow us to determine the labels associated with the wines, as no data about grape types, wine brands, wine selling prices, etc. are included. More information may also allow us to draw conclusions on the grape's region of origin, climate, and type. Perhaps with these types of predictors, the quality of wine may be more accurately predicted. 
