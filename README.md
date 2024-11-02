# immo-eliza-ml
Predictive model for house pricing

# Feature selection

The result of the previous stages of this project was a dataset with multiple features removed (due to too many missing values), that turned out to have a low to moderate correlation with the price. For the modelling, I decided to use the larger 'sample dataset', removing all rows with missing values, ending up with slightly more listings, and more features to input.
The loss of the majority of house listings means a less accurate prediction compared to the original sample dataset, but still is a better starting position than the set from the project.
multiple imputation (iterating over different imputation methods, checking prediction score) to get the best possible estimation of missing values > more house listings > better accuracy.

The assumption of complete data would pose a problem in a real-life situation where not all features are provided;
all possible combinations of value/no value for each variable, deciding on the best model for each situation, decision tree after input
also research: some variables become more important in for ex higher price range? > different pred model

columns dropped, and why
rows deleted for each variable
total rows: from 75511 to 13040

Conclusions from previous stages: correlation, importance of variables


# using province instead of postal code/ geo tags
working with postal code would be much more accurate, certainly for regions with high price fluctuation (ex Knokke in W flanders)
or: with 'gemeente' (+- 300 instead of +- 1000), combining postal codes means not as many needed

most accurate: geo locations, comparing to nearest known houses

Brussels as province
provinces as ordinal

# limitations
location:
outliers like Knokke in West Flanders result in inaccurate predictions. better would be: postal codes/gemeentes instead of provinces, or geo-location (calculate distance to nearest listings). But for this, we would need more instances per location


