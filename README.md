# Objective
The objective of the code is to accurately predict property values in Cook County. For my analysis, I developed machine learning models on historical property value to arrive at accurate predictions using R. 

# Methodology
I conducted my analysis on R by implementing the following steps to achieve my objectives:
A.	Overview of the Data: The historical data had 50,000 observations and 64 variables, out of which ‘sale_price’ was my outcome variable. The outcome variable had a wide range with an average of 298,742, a standard deviation of 315,657 and was skewed to the right, indicating potential outliers. 

B.	Data Cleaning: The data required three broad steps for cleaning and making it ready for analysis. First, several predictor variables were recorded as numeric data types when in fact they were categorical. Therefore, I converted them to categorical variables. Second, 22 variables were eliminated based on three criteria: non-predictive status, inconsistency or unreliability as recorded in the ‘var_is_predictor’ and ‘var_notes’ columns of the codebook, and redundancy due to collinearity (eg: ‘meta_nbhd’ is derived from ‘meta_town_code’). Third, missing values were addressed by a three-pronged approach; (i) variables with more than 25% missing data were excluded as they were unlikely to have predictive value, (ii) since the next three variables with the highest missing data (about 14%) were categorical, I imputed their value using mode as the central tendency. Imputation was necessary to ensure I do not lose the information stored in the other fields of these rows, and; (iii) rows where less than 1% of the data was missing were deleted. At this stage, the data had 49687 observations and 37 variables.
C.	Variable Selection: Since the data had a large number of predictor variables, with potentially irrelevant ones, I decided to perform variable selection using lasso regression. Lasso regression was chosen because it performs well with a large number of variables owing to (i) its ability to shrink the coefficients of unimportant variables to zero; (ii) in-built creation of dummies for categorical variables (which were the most common in the data), and (iii) it is not affected by collinearity or outliers while shrinking coefficients. This helped me identify 27 relevant predictors. 
 
D.	Building ML model: I selected Random Forest method for creating my predictive mode as its flexibility ensures high prediction accuracy. It is very efficient in handling complex relationships within my diverse data and mitigating overfitting, making it well-suited for predicting property values. I trained the model on the selected variables and evaluated its performance, surveying the important variables, and plotting the model. 

E.	Testing Model Performance: The testing model performance involved calculating the Mean Squared Error (MSE) and creating scatter and residual plots to visualize the model's accuracy.

F.	Generating predictions: I preprocessed the "predict_property_data.csv" dataset in the same way as the historical data, that is, converting to categorical variables, imputing missing values, and sub-setting for only the 27 relevant predictor variables. I then generated the predictions using the trained Random Forest model. 


