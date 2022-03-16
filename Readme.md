**Competiton link: https://www.kaggle.com/c/ammi-bootcamp-kaggle-competition**
**Kaggle notebook link: https://www.kaggle.com/paritoshharora/paritosh-101903069-ds-labevaluation**
1. **Data Analysis**
   1. When observed the training data had 13 columns including ‘price’
   2. First the data was analyzed manually and it was observed that it had some irrelevant features such as ‘title’,’id’,’taster\_twitter\_handle’,’taster\_name’; test data also had an ‘index’ column which was irrelevant. These columns are irrelevant because they hold no significance in predicting the price of wine. Hence these were dropped
   3. After dropping we were left with null values in the both the datasets
2. **Data Preprocessing**
   1. Now the columns having these consisted of region\_1,region\_2,country etc
   2. Now out of these region\_2 had the most null values and had less correlation hence it was dropped.
   3. Now for the rest of categorical columns filling them with mode/median doesn’t make sense as these are interrelated. For example a country A if it has missing region\_1 we just can’t fill it with mode as it can be of any other country also. So we fill these values by ‘missing’ hence giving them the same weight.
   4. Now description feature was pending, the problem with this was that you can’t encode it or anything
   5. So I went ahead with “sentiment analysis” . I used nltk’s inbuilt library to classify each description into negative, positive and neutral. Relevant weights of 0,1,2 were given to negative,neutral and positive respectively.
   6. Before directly feeding the text to the inbuilt library the text was preprocessed, stopwords and punctuations were removed to have better results.
   7. Now my training and testing dataset had categorical values and only one number value ‘points’
   8. Outlier analysis was done on numerical feature using binning and no outlier was found
   9. Categorical values were manually encoded, encoding was done on training data first and the values were given with respect to price. This was done to avoid giving any unjustified weight to a particular value.
   10. After training the same dictionary was used to encode testing data, although testing data had some unique values which were not present in training data so they were encoded by using median.
3. **Algorithm Comparison**
   1. We were required to predict price of wine, hence regression algorithms were to be used
   2. Firstly, the testing data was scaled
   3. Then it was splitted in test and train
   4. Earlier in the lab we have also worked with linear regression, ridge regression etc.
   5. So I created a model using linear regression, ridge regression, lasso regression and random forest regression. All of these were implemented using cuML.
   6. Hyper Parameters were tuned, there was no significant difference in the cases of linear,ridge and lasso regression.
   7. When I tuned hyperparameters of Random Forest regressor considerable changes were observed, the score value kept increasing as I increased the number of bins and number of estimators. Score increased from 0.86 to 0.92.

*It was observed that Random forest regressor was the best option*

4. **Model Building**
   1. Now it was time to build the final model.
   2. Instead of splitting train\_gdf, the entire training data was used to train the model with previously found best parameters and algorithm
   3. Test data was scaled and transformed using the previously created scaler only
   4. Model was built and prediction was made on test data
5. **Evaluation**
   1. The predicted values were put in a data frame
   2. Id column of test data was extracted and also put
   3. This data frame was converted to a csv and submission was made
   4. I made several submissions after making changes to the codes
 Score improvement is seen after each submission






