# Group 17 
# Project Description

## King County House Sales Analysis & Regression Modeling
### Project Overview

### Business Problem

The real estate agency, Amani is facing a challenge in providing valuable advice to homeowners regarding home renovations. Homeowners often inquire about the potential increase in the estimated value of their homes after making specific renovations or improvements. The agency needs to develop a predictive model that can accurately estimate the impact of various renovation projects on a home's market value within the northwestern county.

The goal is to offer data-driven recommendations to homeowners, enabling them to make informed decisions about which renovations to undertake and how these renovations will affect the resale value of their homes.

The questions to be answered are:

  1. How does the number of bedrooms, bathrooms, grade and square footage of a house correlate with its sale price in King County?
  2. How much can a homeowner expect the value of their home to increase after a specific renovation project?
  3. Which renovation projects have the most significant impact on a home's market value in the northwestern county?
  4. Are there specific combinations of renovation projects that provide an interdependent effect on a home's market value?

### Analysis Overview
* **Data Understanding**

* **Data Cleaning and Preparation.**

* **Data Visualization.**

* **Modelling.**

* **Interpretation of Results**

* **Conclusion**

* **Recommendation**

### Data Understanding

This project uses the King County House Sales dataset, found in kc_house_data.csv. The file contains information on over 21,000 housing units. The data is organized into a data frame with several columns containing information on the housing units. The columns we used in the analysis are:

 * price - Sale price (prediction target) Predictor Variable
 * condition - How good the overall condition of the house is. Related to the maintenance of the house.
 * bedrooms - Number of bedrooms
 * bathrooms - Number of bathrooms
 * sqft_living - Square footage of living space in the home
 * floors - Number of floors (levels) in house

### Getting Started
Upon carefully choosing, analyzing, cleansing, and generating descriptive statistics, we developed several visualizations that elaborately showed the correlation of each feature in relation to price. These visual representations stem from the selection of relevant columns in our dataset and offered valuable insights for the project.

## Visualization

![Screenshot 2023-09-10 193707](https://github.com/frankkiptoo/phase-2-project-group-17/assets/133040810/12ca04c2-be51-4b34-8d56-873db2897a99)


From the above scatter plot, we observe that sqft_living has a continuous positive correlation with price.

![Screenshot 2023-09-10 193826](https://github.com/frankkiptoo/phase-2-project-group-17/assets/133040810/d1551170-6bc9-443f-8826-5beb555b2e97)

From the bar plot above we observe that houses in very good condition are the most expensive, while the ones in fair and poor condition are the most affordable, therefore the better the condition of the houses the higher the price. 

## Modeling

### Baseline Model: Simple Linear Regression
![Screenshot 2023-09-10 193913](https://github.com/frankkiptoo/phase-2-project-group-17/assets/133040810/d8343a8b-eec7-43b4-9867-433389aec437)

For our multiple linear regression, we built a simple linear regression to be the baseline in order to evaluate our model.

Since sqft_living was the feature with the strongest correlation, we built a simple linear regression with that. We built a simple linear regression model (Model: OLS) with 'sqft_living' as the only independent variable. From our model, for each additional square foot of living space, the 'price' is expected to increase by 280.863 units when all other factors remain constant.


### Simple Linear Regression Visualization

![Screenshot 2023-09-10 194015](https://github.com/frankkiptoo/phase-2-project-group-17/assets/133040810/b0e18798-1b61-42af-93c6-97be39f484fd)

### 2nd Model: Adding another Independent variable

The second model was a multiple linear regression model (Model: OLS) with 'sqft_living' and 'bedrooms' as independent variables.
The multiple linear regression equation based on our model was:

price = 91,770 + (317.6347 * sqft_living) - (62,950 * bedrooms)

This equation represents the relationship between the 'price' of a house and its square footage of living space ('sqft_living') and the number of bedrooms ('bedrooms'). Each coefficient represents the change in the 'price' associated with a one-unit change in the respective independent variable, holding all other variables constant.

### Model Fit

![Screenshot 2023-09-10 194117](https://github.com/frankkiptoo/phase-2-project-group-17/assets/133040810/4672b6d6-aba0-460c-8d08-908ee9bf0ba5)

The plot above shows the true (blue) vs. predicted (red) values, with the particular predictor (in this case, sqft_living) along the x-axis.

![Screenshot 2023-09-10 194607](https://github.com/frankkiptoo/phase-2-project-group-17/assets/133040810/dbfa97df-88cd-4b65-8b52-69a4541999e6)

The plot above shows the fit for the other predictor, bedrooms

### Partial Regression Plot / Plotting Residuals

![Screenshot 2023-09-10 195059](https://github.com/frankkiptoo/phase-2-project-group-17/assets/133040810/912baa63-557f-4b15-a7bf-b80d9416a160)

The above image shows a plot of the regression with the "sqft_living" as the exogenous variable

![Screenshot 2023-09-10 195133](https://github.com/frankkiptoo/phase-2-project-group-17/assets/133040810/fcfd43c8-4646-4af4-8210-4b8be3b0072d)

The above image shows a plot regresion of exogenous variable against bedrooms

### 3rd Model: Multiple Regression with Many Features including the One-Hot Encoded Variables

Since we have a model with 1 predictor (sqft_living) as well as a model with 2 predictors (sqft_living and bedrooms), we tried a model that uses all of the available numeric columns as features. The model was a multiple linear regression model (Model: OLS) with eight independent variables.
So, the multiple linear regression equation based on this output is:

price = 44,920 + (311.64 * sqft_living) + (11,990 * bathrooms) - (67,170 * bedrooms) + (17,060 * floors) - (4768.5025 * condition_Fair) + (49,570 * condition_Good) + (44,370 * condition_Poor) + (122,500 * condition_Very Good)

This equation represents the relationship between the 'price' of a house and multiple independent variables, including square footage of living space ('sqft_living'), the number of bathrooms ('bathrooms'), the number of bedrooms ('bedrooms'), the number of floors ('floors'), and four categorical variables representing different conditions ('condition_Fair', 'condition_Good', 'condition_Poor', 'condition_Very Good'). Each coefficient represents the change in the 'price' associated with a one-unit change in the respective independent variable, holding all other variables constant.

![Screenshot 2023-09-10 195218](https://github.com/frankkiptoo/phase-2-project-group-17/assets/133040810/6d18082b-30cc-4ca0-a5c7-07d199752158)

The avove plot shows partregress grid using third_results as the model

## Conclusion 
Based on the provided interpretation of the three model results and the business problem faced by the real estate agency Amani, we can draw the following conclusions

  1. Baseline Model:
The baseline model, which includes only the 'sqft_living' variable, has an RMSE of approximately 261,655 USD and an R² of 0.4927. While it provides a basic estimate of home prices, it has room for improvement in both prediction accuracy and explanatory power.

  2. Second Model:
The second model, incorporating 'sqft_living' and 'bedrooms,' shows a slight improvement over the baseline. It has a lower RMSE (approximately 257612.12 USD) and a slightly higher R² (0.5082). However, further enhancements are possible.

  3. Third Model:
The third model, including all chosen independent variables, performs the best among the models. It has the lowest RMSE (approximately 255203.69 USD) and the highest R² (0.5174). This model demonstrates the highest prediction accuracy.

The best model chose out of the three is the third model because of:

  1. Model Performance:

The third model, which incorporates 'condition,' 'bedrooms,' 'bathrooms,' 'sqft_living,' and 'floors,' exhibits the best overall performance among the models considered.

  2. Prediction Accuracy:

The third model has the lowest Root Mean Squared Error (RMSE) of approximately 255203.69 USD, indicating the highest prediction accuracy among the models. This means that the model's predictions are, on average, the closest to the actual sale prices.

  3. Explanatory Power:

The third model also has the highest R-squared (R²) value of approximately 0.5174, signifying the greatest explanatory power. It explains about 51.74% of the variance in home prices, suggesting that it provides the most comprehensive understanding of the factors influencing sale values.

The model built offers a valuable tool for the agency to formulate effective pricing strategies. It provides coefficients associated with each feature, allowing the agency to make more precise price estimates based on a property's specific attributes. Additionally, by comparing these estimated prices to real-world prices, the agency can spot instances where properties are priced too high or too low, enabling them to make appropriate adjustments to optimize their sales potential.

## Recommendations
Based on the the business questions and objectives of the project and the third model, which includes 'condition,' 'bedrooms,' 'bathrooms,' 'sqft_living,' and 'floors,' the following are detailed recommendations for the real estate agency Amani:

  1. Estimating the Impact of Specific Renovation Projects:
The agency can use the Third Model to provide homeowners with estimates of how specific renovation projects will impact the resale value of their homes. This will assist homeowners in estimating the impact of specific renovations, create a user-friendly interface or tool where homeowners can input details about their renovation plans, such as the number of bedrooms, bathrooms, the condition of the property, square footage of living space, and the number of floors. The model can then generate predictions of the expected increase in home value after these renovations. Homeowners can make informed decisions about which renovation projects to prioritize, based on their expected return on investment (ROI). This will empower homeowners to invest in renovations that will maximize their property's resale value.

  2. Identifying Renovation Projects with the Most Impact:
Amani can utilize the third model to identify which specific renovation projects or features have the most significant impact on a home's market value in the northwestern county. They can conduct a feature importance analysis using the third model. This analysis can highlight which variables (e.g., bedrooms, bathrooms, condition) have the most substantial influence on home prices. The model can then provide rankings or insights into which renovations or property features contribute the most to home value. By identifying the most impactful renovation projects and features, the agency can guide homeowners toward investments that are likely to yield the highest returns. This can also inform marketing strategies and property listings for sellers.

  3. Correlation of Bedrooms, Bathrooms, Grade, and Square Footage with Sale Price:
They can leverage the third model to explain how the number of bedrooms, bathrooms, the grade of a house, and its square footage correlate with its sale price in King County. They can utilize the model's coefficients and feature importance analysis to explain the correlations between these variables and sale price. This will provide homeowners and buyers with insights into how each of these factors influences home prices, allowing them to make more informed decisions. Homeowners can understand which property features are highly valued in the real estate market, potentially guiding them in making renovations or improvements that align with market preferences. Buyers can use this information to assess property values based on their preferences and requirements.

  4. Identifying Combinations of Renovation Projects:
The third model will help identify specific combinations of renovation projects that provide an interdependent effect on a home's market value. They can use the model to analyze the effects of combining different renovation projects. Identify combinations that result in combined effects on home values. This will provide homeowners with recommendations on the combinations of renovations that may maximize their property's resale value.

These recommendations align with the agency's goal of offering comprehensive guidance and enhancing decision-making for clients in the real estate market.

## Summary
In summary, the project study suggests that the number of bedrooms, square footage of living area, condition, number of bedrooms, bathrooms and floors are important factors to consider when determining the price of a home. However, it is essential to consider other market factors and property-specific attributes in conjunction with the findings of this analysis to arrive at an accurate and competitive listing price such as architectural style, lot size and landscaping, upgrades and amenities, historical sales data, market trends, school district, crime rate, zoning and regulations.
