# Wine Quality Prediction
Wine Quality Prediction Project
## Table of contents
* [Introduction](#introduction)
* [Technologies](#technologies)
* [Goal](#goal)
* [Dataset](#dataset)
* [Models Used](#models-used)
* [Methodology](#methodology)
* [Model Results and Selection](#model-results-and-selection)
## Introduction
I was first introduced to wine during a wine tasting trip I took to Italy in 2010. We visited many cities such as; Milan, Florence, Tuscany, Venice, etc. in which we visited vineyards, drank wine, ate delicious food, and were taught about the wine making process. Through my experience in Italy, I became a fan of wine specifically red wine. I wanted to take a deeper dive into what the components are for a high quality wine. 
## Technologies
Python
## Goal
The goal for this analysis is to be able to predict the quality of wine based on certain attributes.
## Dataset
The dataset can be found here:
<br>
https://archive.ics.uci.edu/ml/datasets/wine+quality<br />
<br>
The data includes 1,599 observations and the following variables:<br />
<br>
**fixed acidity:** The predominant fixed acids found in wines are tartaric, malic, citric, and succinic. Wines produced from cool climate grapes are high in acidity and thus taste sour. These high-acid wines can be treated to reduce the acidity.
<br>
**volatile acidity:** Acetic acid, which is also the primary acid associated with the smell and taste of vinegar.
<br>
**citric acid:** An acid supplement during the fermentation process to help winemakers boost the acidity of their wine especially grapes grown in warmer climates.
<br>
**residual sugar:** Natural grape sugars leftover in a wine after the alcoholic fermentation finishes.
<br>
**chlorides:** Contributes to potential salty taste in wine.
<br>
**free sulfur dioxide:** Measure of the amount of SO2 that is not bound to other molecules. Sulfur Dioxide is used throughout all stages of the winemaking process to prevent oxidation and microbial growth.
<br>
**total sulfur dioxide:** The portion of SO2 that is free in the wine plus the portion that is bound to other chemicals in the wine such as aldehydes, pigments, or sugars.
<br>
**density:** Density of wine is primarily determined by the concentration of alcohol, sugar, glycerol, and other dissolved solids.
<br>
**pH:** Way to measure ripeness in relation to acidity.
<br>
**sulphates:** Food preservative widely used in winemaking in order to maintain the flavor and freshness.
<br>
**alcohol:** The amount of alcohol the wine contains.
<br>
**quality:** How the wine is rated. In this dataset the lowest quality is 3 while the highest is 8.
![Dataview](./img/dataview.png)

## Models Used
Linear Regression: Baseline Model
<br>
KNN
<br>
Random Forest

## Methodology
1. *Data Understanding and Data Cleaning:* Lengths and types of the variables were determined and data was checked for missing values. The dataset consists of all numeric variables. The dataset doesn't contain missing values.

2. *Exploratory Analysis:* Created visualizations to explore the target variable and examine the potential existance of outliers or corrupt data. Further visualized the relationship between the target and the feature variables and relationships between features.<br />

First, I examined the target variable, quality. The average of wines in this dataset are rated 5 or 6 and target variable is normally distributed.
![Targetviz](./img/targetplot.png) <br />

Second, a distribution plot and a box plot was created to examine the distribution of each feature and the interaction between feature and target respectively. 
![Featplot](./img/featplot.png) <br />

Lastly, a heatmap was created to further examine the degree of correlation between varibles.
![Heatmap](./img/heatmap.png) <br />

The highest positively correlated variables are:
* citric acid and fixed acidity
* density and fixed acidity
* alcohol and quality <br />

The highest negatively correlated variables are:
* citric acid and volatile acidity
* pH and fixed acidity
* pH and citric acidity
* denisty and alcohol <br />

3. *Feature Selection and Feature Engineering:* In order to access which features to use for the linear regression model, I reviewed the p-values for each feature in order to determine with features showed staistical significance. I applied backward elimination in order to select the best features for the model. The variance inflation factor shows that mulicollinearity does not exist in the model selected. For the random forest model, I applied binning to quality. Wines of quality 3-4 were considered as low, 5-6 were considered medium, and 7-8 were considered high quality. <br>
![Selfeatures](./img/selfeatures.png) ![Vif](./img/vif.png) <br />

4. *Model Building and Evaluation:* Established a baseline model and developed two additional models to see if I could improve upon the baseline. For each model a train-test split of 70%-30% was used. Each models were then fitted. <br />

### Baseline Model: Linear Regression
![Regressionplot](./img/regressionplot.png) <br />
  *MSE:* .39 <br>
  *R-squared:* 38% <br />
### KNN
![Knn](./img/knn.png) <br />
  *MSE:* .44 <br>
  *Accuracy:* 67% <br />
### Random Forest
![Randomforest](./img/randomforest.png) ![Distplotrf](./img/distplotrf.png) <br />
  *MSE:* .18 <br>
  *Accuracy:* 82% <br />

5. *Scoring the Dataset:* Evaluated the performance of each model based on MSE and R-squared/Accuracy. The model with lowest MSE and highest R-squared or Accuracy was selected for quality prediction.

## Model Results and Selection
**Random Forest gave the best prediction of quality with MSE of .18 and Accuracy of 82%.**
The distribution plot for the choosen model shows that the predicted values are very close to the actual values with a bit of an overestimation in salaries from $105,000 to $150,000.<br />
<br>
The plot below demostrates the level of importance of each feature on the quality of wine. The feature with the highest influence on quality is alcohol.
![featimp](./img/featimp.png)<br />
