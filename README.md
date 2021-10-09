# Real-Estate-Price-Predictor
This project uses data from the Aimes housing dataset to predict real estate pricing 
SIR - Project 2


Problem Statement
A homeowner with multiple properties is looking to sale some houses in Ames, IA and they want to know what prices to expect. They have enlisted me to to predict what prices their properties will sale for.


Data

The following dataset was used to perform the analysis for the above problem. It is data pertaining to real estate in Ames, IA

train = pd.read_csv("./projects/project-02/datasets/train.csv")

The dataset included 2051 rows of data from 81 different columns of features


Data Cleaning

All columns that had any missing values were dropped from analysis and following this the dataset consisted of 2051 rows of data from 55 different columns. 

The columns "Id" and "PID" were dropped because their values are arbitrary and do not contribute to the mathematical analysis of our variable of interest. Then the varibles'MS SubClass', and 'Mo Sold' were all transformed from integers into objects so that they would not be mathematically analyzed because in this case their numerical values are representations of catagorical values.


EDA

The distribution of correlation to 'Salesprice' shows that the highest correlation to salesprice include the features "Overall Qual" = .8 correlation, "Gr Liv Area" = .69 correlation, "1st Fl SF" = .62 correlation, "Year Built" = .57 correlation, "Year Remodel/Add"= .55 correlation, "Ful Bath" =.53 correlation and "TotRms AbvGrd" = .5 correlation.

A "features" group was made consisting of all of the variables that were the most highly correlted to the SalePrice. All the variables within "features" show a normal distribution with the excpetion of 'Year Built'and 'Year Remod/Add'

"features" was set as the X variable and train[SalePrice] was set as the y variable

Modeling

Model 1

Using Train-Test-Split The data was split into a testing portion and a training portion. 70% of the data became the training set and 30% of the data became the testing set. 

The X variable from the training data was tranformed using StandScaler
 
The Transformed X was fit to a Linear Regression with the y variable in the training data

That test returned R-squared values of 0.7594495047826644, 0.8196171317265603 for the training and testing data respectively. This showed that the model was underfit because it performed better on the testing data than the training data.

The transformed X varible was then fit to a Ridge Regularization model and the R-squared scores on the training and testing data were 0.7593659281801862, 0.8189037615439254 respectively.

The transformed X variable was then fit to a Lasso Regularization model and the R-squared scores on the training and testing data were 0.7594488920933378, 0.8195853951316083 respectively.

The transformed X fit to the Ridge regularization was the model used for predictions and the MSE for the training and testing data were 1541596088.5311625, 1082489542.6597185.

The plot of the residuals shows linearity and homoscedasticity showing that the model is fair. And the R^2 values as well as the MSE show the same.

Model 2

Using Train-Test-Split The data was split into a testing portion and a training portion. 70% of the data became the training set and 30% of the data became the testing set. 

The X variable from the training data was tranformed using Polynomial features and additional interaction columns were added. Following this X went from containg 7 features to now containing 35 features.
 
The polynomial X was fit to a Linear Regression with the y variable in the new training data

That test returned R-squared values of 0.8675867607250278, 0.8721864539946889 for the training and testing data respectively. This showed that the model was very slightly underfit because it performed better on the testing data than the training data.

The polynomial X varible was then fit to a Ridge Regularization model and the R-squared scores on the training and testing data were 0.8659265518580349,0.8736244377984129 respectively.

The transformed X variable was then fit to a Lasso Regularization model and the R-squared scores on the training and testing data were 0.8610957477173592, 0.8698289098157456 respectively.

The polynomial X fit to the Ridge regularization was the model used for predictions and the MSE for the training and testing data were 858927007.5864649, 755400695.7695158.

The plot of the residuals shows linearity and homoscedasticity showing that the model is fair. And the R^2 values as well as the MSE show the same.

Conclusions 

Model 2 was a better predictor of the SalePrice and it shows that when predicting selling price in Ames,IA the most important features are:

Year Remod/Add : $ -9401.535226  

Overall Qual Full Bath: $ -6477.499430 

Year Built: $4850.314955 

Overall Qual TotRms AbvGrd: $2234.494347


Recommendations

Incorporating catagorical features into the model could definitely add strength

Imputing values instead of dropping could lead to a stronger model

More research into interpreting interactions and how they work together will allow you to give the client more concise steps in case they want to add value.
