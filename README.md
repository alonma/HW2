# Meachine Leraning with R - Titanic database

   Alon Maharshak 302955851  
   Miriam Hazanov 204500763  
   Kaggle UserName: Miri92 


## Data Preperation
  We manipulated the data in a way that will work for all Algorítem
  we used these libaries: 
  1. library('ggplot2') # visualization 
  2. library('ggthemes') # visualization
  3. library('scales') # visualization
  4. library('dplyr') # data manipulation
  5. library('mice') # imputation 
  
  We edited some columns like title, name and family size to get a better understaing of the data: 
  
![Image of Data Prep](https://github.com/alonma/HW2/blob/master/DataPrep.JPG)



## First Try - RPart
Our first try was with RPart, we used a training set with size of 95% and use only part of the columns for the formula.
![Image of RPart Code](https://github.com/alonma/HW2/blob/master/RPart-Code.JPG)

Our grade with these try was 0.79904
![Image of LeaderBoard](https://github.com/alonma/HW2/blob/master/RPart-Grade.jpg)
First results(https://github.com/alonma/HW2/blob/master/try-Rpart.csv)


## Second Try - Random Forest

Our seconed try was with Random Forest, we used a training set of 75% and we used some more columns that improved the scores, we had to address some Null values issues since RF doesn't know how to handle Nulls, we used one tree since we don't have a lot of attributes to address.
![Image of Random Forest Code](https://github.com/alonma/HW2/blob/master/RF-Code.JPG)

Our grade was 0.78469
![Image of LeaderBoard](https://github.com/alonma/HW2/blob/master/RF-Grade.jpg)
Second results(https://github.com/alonma/HW2/blob/master/try-RF.csv)


## Third Try - Ensamble Caret

Our third try was a combanation of Generalized linear model with a Caret ensamble method. we added the Caret step, creating a model and then predictin with the GLM method.

![Image of Caret Code](https://github.com/alonma/HW2/blob/master/Caret-Code.JPG)

Our grade was 0.765
![Image of LeaderBoard](https://github.com/alonma/HW2/blob/master/Caret-Grade.jpg)
Third results(https://github.com/alonma/HW2/blob/master/try-Caret.csv)

