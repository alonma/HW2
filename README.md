# Meachine Leraning with R - Titanic database
**Alon Maharshak 302955851  
Miriam Hazanov 204500763**  

## Data Preperation
  We manipulated the data in a way that will work for all Algorítem
  we used these libaries: 
  1. library('ggplot2') # visualization 
  2. library('ggthemes') # visualization
  3. library('scales') # visualization
  4. library('dplyr') # data manipulation
  5. library('mice') # imputation 
  
  We edited some columns like title, name and family size to get a better understaing of the data: 
  
  ** 
  df$Title <- gsub('(.*, )|(\\..*)', '', df$Name) 
  rare_title <- c('Dona', 'Lady', 'the Countess','Capt', 'Col', 'Don', 'Dr', 'Major', 'Rev', 'Sir', 'Jonkheer') 
  df$Title[df$Title == 'Mlle']        <- 'Miss'  
  df$Title[df$Title == 'Ms']          <- 'Miss' 
  df$Title[df$Title == 'Mme']         <- 'Mrs'  
  df$Title[df$Title %in% rare_title]  <- 'Rare Title' 
  df$Surname <- sapply(df$Name, function(x) strsplit(x, split = '[,.]')[[1]][1]) 
  df$Fsize <- df$SibSp + df$Parch + 1 
  df$Family <- paste(df$Surname, df$Fsize, sep='_') 
  df$FsizeD[df$Fsize == 1] <- 'singleton' 
  df$FsizeD[df$Fsize < 5 & df$Fsize > 1] <- 'small' 
  df$FsizeD[df$Fsize > 4] <- 'large' 
  df$Cabin[1:28] 
  strsplit(df$Cabin[2], NULL)[[1]]  
  df$Deck<-factor(sapply(df$Cabin, function(x) strsplit(x, NULL)[[1]][1])) **


## First Try - RPart
Our first try was with RPart, we used a training set with size of 95% and use only part of the coulms for the formula.

  tmp<- sample(1:nrow(df),nrow(df)*0.95) 
  train <- df[tmp,] 
  test <- df[-tmp,] 
  library(rpart) 
  set.seed(123) 
  rfit <- rpart(Survived ~ Pclass + Age + Sex + Fare + Embarked,
              data=train,
              method="class") 
  nw_df <- read.csv('test.csv' , na.strings = "") 
  ids <- new_df$PassengerId 
  new_df$Pclass <- as.factor(new_df$Pclass) 
  Prediction <- predict(rfit, new_df, type = "class") 
  submit <- data.frame(PassengerId = ids, Survived = as.character(Prediction)) 
  write.csv(submit, file = "try2.csv", row.names = FALSE) 

Our grade with these try was 0.79904
![Image of LeaderBoard](https://github.com/alonma/HW2/blob/master/RPart-Grade.jpg)

## Second Try - Random Forest

## Third Try - Ensamble Caret

