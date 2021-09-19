Our company, ACME Housing Inc, is a small housing investment company that earns the majority of its revenue by purchasing and renting units, while flipping units that have grown appreciably in the market and continuously investing into underpriced units in the market.

They are looking to expand their market share in Iowa. They will begin by dipping their toe in the housing market in Ames County, Iowa and have recently purchased detailed information on all house sales in the year of 1998. With this new information, they would like us to design a predictive model that would be able to help determine the base value of houses being sold on the market to ensure they continue to purchase advantageous lots and are not overpaying.

Ideally, this model would allow us to:

1.  Determine the underlying value of houses in the Ames, Iowa region
2.  Identify which features are key and contribute the most to housing prices, and as a result will be most desirable to renters
3.  Determine if specific types of housing are more popular in Ames, in the case that ACME decides to purchase and build a housing development

---

## Datasets
*  [`train.csv`](./datasets/train.csv): Training Data from the Ames, Iowa Housing Dataset
*  [`train_final.csv`](./datasets/train_2.csv): Cleaned Ames Iowa Housing Training Data
*  [`new_test.csv`](./datasets/new_test.csv): Test Data from the Ames, Iowa Housing Dataset (Saleprice Removed)
*  [`new_test_2.csv`](./datasets/new_test_2.csv): Cleaned Ames Iowa Housing Test Data
*  [`train_1.csv`](./datasets/new_test.csv): Train Data from the Ames, Iowa Housing Dataset for Modelling Use, 70% of Training Data
*  [`validate_1.csv`](./datasets/new_test_2.csv): Cleaned Ames Iowa Housing Validate Data for Modeling Use, 30% of Test Data
*  [`y_pred.csv`](./datasets/y_pred.csv): Saleprice Predictions from the Test Data

---

### Analysis

Data from the Ames Housing market was cleaned and data imputed where needed. It was then analysed for correlations between each variable and the saleprice, as well as between each other for collinearity, to determine if it would contribute to our model.

#### Model Summary

The best model ended up being the 5th Model tested, a Lasso Regression with 38 Variables, including 2 engineered features. While model 5 did not have the best RMSE with a score of 29692 on the test set, but it came very close, while also trimming off 9 features off the best model for a total of 38.

As the housing industry is still very much an industry that lives offline, trained housing appraisers still have to go house to house to gather information. This is confounded by the fact that many variables are ranked on an ordinal scale, or a subjective scale, and therefore would see a great degree of variance based on the appraiser. The fewer variables we use, the less we are subjected to this.

A delicate balance also needs to be struck between time and capital spent, and the accuracy of the model. With less variables, less time will be spent per house and more money will also be saved on manpower.

---

### Conclusions

#### Most Important Features

Unsurprisingly, the two largest continuous features that contribute to housing costs are above ground living space and total basement size. With each increase in 1 square foot, leading to an increase in cost by 20775 and 18305 respectively.

Unfinished basement square footage was one of the largest detractors of house pricing. One strategy might be to look into houses that are ideal but have large unfinished basements, if the cost of redo-ing or finishing the basement is less than the "discount" on the price.

#### Desirable Additions

Interestingly, full baths in the house were negatively correlated with house prices, which does give the impression that they are generally not view favourably. Obviously, full baths are required, and more so based on the number of rooms there might be but perhaps the information suggests that more than necessary is not welcome.

This suggests that people generally prefer having a greater amount of living space, or useable space, rather than having it taken up by unnecessary features. It may also be that people tend to prefer more modern fixings, as people do pay more for better quality heating versus the fireplace.

Garages also increase the price of the house, although having an attached garages saw a decrease. It isn't unusual considering that Ames is not a large city and vehicle ownership is correlated with suburban centres in America. In the case of building a large apartment complex, it does point to the need for a large carpark area, to accomodate all possible vehicle owners in the complex.

Lastly, wooden decks are also seen as positive additions. One possible contributing reason for this, is the love of Americans for backyard barbecues on their decks.

### Further Steps

Unfortunately, the test set contains limited data and data that is somewhat outdated at this point, especially considering the recent rise in house sales and prices in the last two years in the US. Further steps to help improve the model would include:

1. Expanding the time frame of the data to include recent years
2. Including rental prices for each house or for similar hosues in the area, so that we can calculate rental prices the houses would also pull
3. One last thing to consider is that student housing is always a steady source of renters. With Iowa State University having a large presence in the town, distance of the house from the university, might be a good predictor of ease of rental in the future.
