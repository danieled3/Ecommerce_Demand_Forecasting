# Ecommerce Demand Forecasting

## Table of Content
  * [Overview](#overview)
  * [Motivation](#motivation)
  * [Technical Aspects](#technical-aspects)
  * [Results](#result)
  * [Technologies](#technologies)
  * [To Do](#to-do)
  * [File List](#file-list)

  
## Overview <a name="overview" />
The aim of this project is to predict the total ecommerce orders of a chain of supermarkets. It allows to estimate orders with weekly detail for the next 25 weeks starting from information about the past trend of orders and number of customers.

In this project I
1. Plot each values to identify particular trends or periodicity
2. Analyze correlation between each negative translations of provided segments and Total Orders to find some relationships
3. Select both best set of features and best model by evaluating some performances indexes
4. Consider some techniques bases on signal analysis and evaluate their performances
5. Make the requested prediction by using the best model

## Motivation <a name="motivation" />
It was an excercise proposed in an inteview process as a take-home assignement. It has be really funny and interesting so I wanted to share it. However, I hided any information abount the company.

## Technical Aspect <a name="technical-aspects" />
In this project the crucial aspects was the features preparation and selection. In particular it was difficult to find periodicities and to understand what time shifts of features time-series to use. The way I proposed to solve the problem was to build a function *delta_corr*. It computes the Pearson correlation between the metric to predict and each negative time shift of the features. After that, I picked only the negative time shifts with the highest correlation. It allows to find periodicities in features and metric too.

Moreover, I exploited *caret* library to build a wide range of models. Then I used criteria based on business needs for model selection.

## Result <a name="result" />
As you can find in the document *Online Forecasting Exercise.pdf*, the performance of the best models on validation set are the following

<img src="https://user-images.githubusercontent.com/29163695/122689340-1e0fb900-d222-11eb-9595-8e2c8df241f1.png" height="200">

where the higher is the value *Subset*, the fewer features are used. 

The best model is the SVM one. In genera, the best models are the simplest ones because the considered features are very suitable to describe how the orders trend changes. 

In the end, I computed a prediction based on Triple Exponential Smooting techique where I used only past values of orders. The performance on the test set are worst than the performance of the SVM model on the same data. Since the SVM model uses not only past values of orders, but also other features, the fact that it performs better than TES means that I am rigth using oter information in estimation.

<img src="https://user-images.githubusercontent.com/29163695/122689658-abeca380-d224-11eb-8a31-72a575f46e5e.png" height="200">

## To Do <a name="to-do" />
This work is only an initial analysis of the Total Orders Forecasting. Some ideas to obtain a better estimate are the following:
* Work more on tuning of neural network and random forest models. They weren't fine tuning in this analysis
* Consider regression models where the relationship with features is not linear
* Train 2 different models to estimate, for example, the first 12 periods and the following 13. This approach would allow to use most recent data to better predict orders of the nearest future.
* Try to obtain further data to explain for example the minimum of TO in period 160.

## File List <a name="file-list" />
* **Ecommerce_Demand_Forecasting.ipynb** Full process built through R markdown. It has the full code and a detailed description of every step.
* **Ecommerce_Demand_Forecasting.pdf** Pdf extraction of the previous file with outputs and charts.

