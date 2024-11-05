# immo-eliza-ml

## Description
After scraping and data analysis, this prediction model is the third step into BeCode's ImmoEliza project, aimed at creating a price prediction model for the Belgian house market.
The starting here is a .csv file with the raw scraped data, used to create a preprocessing pipeline and train a machine leraning model, with the ability make price predictions on newly imported data.

## Installation
Before predicting prices, make sure to install the requirements:

pip install -r requirements.txt

## How to use
### Training the model
1. Place your dataset in the folder 'data', and make sure to rename it to 'properties.csv'. This file should have the same columns as the original training data.
If you only have properties to be predicted, you can skip this step.

2. Run the script. It will print out a summary before and after cleaning and preprocessing, similar to the one in the screenshot below (example after cleaning):
(image)
By comparing these two you can monitor the modifications to your dataset, and doublecheck if everything went as expected.
Note that all empty values and values containting "MISSING" should be removed, except for the variable 'surface_land_sqm'; the remaining empty values here are apartment listings, but those will be taken care of later.

Along with the summaries, the script will print out statements after each action taken, enabeling you to closely monitor each step.

3. The scores for the model will be printed out for you to check its accuracy. At the end of the process, the it will be saved into two seperate files, 'model_file_house.pkl' and 'model_file_apartment.pkl' in the 'models' folder.


### Predicting house and apartment prices
1. Make sure that the 'models' folder contains two files, one for apartments, and one for houses.
2. Put your data with the listings to predict in the 'input' folder as 'new_data.csv'. Dont forget to update the filename in the script.
Make sure that your dataset has the same schema as the original training set!
3. Run the script. Your price predictions will be presented as a DataFrame.


## Limitations
### Only for 'family residences'
To avoid outliers, the model was only trained for properties below 1 000 000 EUR, and maximum 5 bedrooms. 

### Incomplete inputted data
When predictions are made on new data, all features should be filled in. If not, the script will look at the new dataset to fill in those blanks. If a specific feature is consistently blank, it will not be able to do that. The larger the set of predictions to be made, the better those results will be.

### Fututre improvements
This model was created in 4 days as a part of BeCode's AI & Data Science program, along with exploring the new study material. This implies that there are still room for a few optimalisations:

- Since I decided to start from a larger dataset, I opted to remove all (a lot!) listings with empty and missing values. This made that the result might be biased (for example, the number of apartments is much lower than the number of houses in the training set). This may affect the accuracy of predictions, and will return a poorer model when training with a smaller dataset.
The solution for this would be (multiple) imputation to fill the blanks (for example with the MIDASpy package).
- Geographical information about the house/apartment is valuable information. For simplicity's sake, i used the 'province' feature for this. For this reason, this model has difficulties with outliers like Knokke.
More accurate would be using the postal codes (given there is sufficient data for each locality), or even better, the latitude/longitude, to the relation between different house prices could be taken into account much better.
Additional data like the presence of public transport, busy roads, schools, public facilities etc. in the vicinity might be a valuable addition.
- Improve the model score: spend more time evaluation (more) models, for example with k-fold cross-validation.
Also revisiting the pre-processing, and better hyperparameter tuning are expected to improve results.
- User convenience: putting the cript in .py files, providing a form to fill in estimation data, and in general more user interaction would be welcomed.

### Brussels area is a province.
I do know it's not, but in this model it's treated as one, since in reality it has a lot in common with other procinces.
