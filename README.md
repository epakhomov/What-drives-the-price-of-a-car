# What drives the price of a car?

## Introduction

This README file provides a summary of findings for Practical Application Assignment II: What drives the price of a car? Please note that this README file is not a non-technical summary required by the assignment. It will be provided at the end of this README and in [the Jupyter book that can be found here](/src/prompt_II.ipynb).

## The objective and the data

The objective of this assignment is to understand what factors make a car more or less expensive. As a result of the analysis, we should provide clear recommendations to your client -- a used car dealership -- as to what consumers value in a used car. The data for this assignment was provided as a subset of original dataset.

## The methods

The methodology for this assignment was based on CRISP_DM framework and included standard ML stages like Business and Data understanding, Data preparation, etc. Please note that only linear regression models were in the scope of the assignment. In addition, while the [Jupyter notebook](src/prompt_II.ipynb) tries to follow the CRISP_DM framework, this README does not. 

## Data quality and data preparation highlights

The data missed significant portion of values in few categories (Fig.3.), it had many duplicates, outliers, etc. It was also establsihed that nuances of data preparation and cleaning had significant effect on the outcoume. Quantifying this effect is a subject of feature research.

<img src="/images/3.png" alt="Fig.3" class="center" style="width:600px;height:auto;">

Standard Pandas deduplication and imputation techniques were used. Non-numeric variables were mean encoded. Outliers were removed empirically. 

## Regression models and performance

The following models were used:
    - Linear regression
    - Ridge regression with default parameters
    - GridsearchCV was used to find optimal alpha for ridge regression
    - Lasso regression with various parameters
    - RidgeCV with target log transformation

Suprisingly, absolutely all models scored roughly the same for both training and test scores with R2 ~ 0.45.

## Feature importance

In order to assess feature importance, coefficients for the linear model were examined (Fig.7.) as well as the SHAP values (Fig.8.).

<img src="/images/7.png" alt="Fig.7" class="center" style="width:600px;height:auto;">

<img src="/images/8.png" alt="Fig.8" class="center" style="width:600px;height:auto;">

## Results and discussion

We can see that there is only one independent variable, "odometer", that has a strong negative relationship with the price target. Which makes sense, the more miles car had driven, the less valuable it becomes.

In terms of effect sizes of the variables, we can see that aside from the odometer variable, there are six more variable that display sizeable effect. 

We get similar results from Shap. As we can see from the Shap plot, the higher odometor values negatively impact the price. While lower values of year also negatively impact the price which also makes sense.

## Next steps

We can try improving the model performance by the following:
    - Improving data preparation and cleaning stages
    - Acquiring more data from the original dataset
    - Applying non-linear models

## Non-technical recommendation to a dealership

Dear sellers,

I'd like to discuss what factors or properties of a used car make it less or more expensive from a buyer's perspective and what you can do it about it. As we all know, different buyers value different things in a car. For example, someone who likes music will be looking at an acoustic system and properties of a car, someone who doesn't like music, wouldn't really care about it that much. Therefore, we will be looking at properties of a car that are important for the vast majority of the buyers. This information should increase sales of the inventory.

According to the analysis, the two most important properties are current mileage and year when the car was made. The bigger value of the odometer is, the lower price a customer is willing to pay for a car. The opposite is also true, customers are willing to pay more money for the cars with lower mileage. Regarding the year of a car, the older car is, less valuable the car becomes from a buyer perspective. Other importance factors that impact the value of a car are the make of a car and the type (sedan, SUV, etc.). The condition of a care doesn't seem to be a strong factor. That's most likely due to the fact (unless the body is visibly damaged), that a true condition of internal important parts of the car(engine, brakes, etc.) is unknown most of the time.***

Based on this analysis, we recommend the following: 

1) Don't let the original sellers to leverage any other properties of a car to get a better deal with you. Remember, the most important properties are current mileage and the year. As an example, If a car was manufactured many years ago and has a lot of miles on it, it doesn't really matter if it has an unusual color. 

2) In order to maximize the revenue, our recommendation is to focus on buying (from the original owners) cars manufactured in recent years and that have low odometer values. The ROI from buying newer cars from owners should be higher than ROI from buying any cars.