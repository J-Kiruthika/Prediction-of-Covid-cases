# Flipr Hackathon 6.0 - 2020

**A Hackathon ML Product**

*12th September 2020 - 14th September 2020 (Online)*

**Team Name:** Maven

**Team Members:**
* [Aishwarya G](https://github.com/izoooo)
* [Balaji Ravi](https://github.com/BalajiRavi63)
* [Kiruthika J](https://github.com/J-Kiruthika)
* [Yashdeep Kumar](https://github.com/yashdeepkumar)

### DataSet

This dataset is a Covid-19 Dataset given as three parts:
1. Variable_Description.xlsx:
    * This file contains description of all the variables available in the dataset
2. Training_data.xlsx:
    * This is the training dataset on which model has to be trained, which contains parameters of a city on 1st September 2020
3. Test_data.xlsx:
    * This is the test data on which accuracy of the model will be computed. It also contains Time Series data of Foreign Visitors to be used for Part – 02
    
**Variables Description**
![Variable Description](/Prediction_plot/variable_desc.PNG)

### Data Review

**Null Values**

We have found that there are null values present in the following Fields
* Population [2011]
* Popuation [2001]
* Sex Ratio
* Median Age
* Avg Temp
* SWM
* Toilets Avl
* Water Purity
* H Index
* Female Population
* \# of hospitals
* Foreign Visitors

**Categorical Variable Fields**
* swm - 3 categories
* city_type - 21 categories

**Continuous Variable Fields**
* population2011 - 739 non-null    float64
* population2001 - 295 non-null    float64
* sex_ratio - 777 non-null    float64
* median_age - 769 non-null    float64
* avg_temp - 770 non-null    float64
* toilets_avl - 761 non-null    float64
* water_purity - 629 non-null    float64
* h_index - 647 non-null    float64
* fem_population - 646 non-null    float64
* hospitals - 772 non-null    float64
* foreign_visitors - 697 non-null    float64
* covid_cases - 787 non-null    float64

### Data Preprocessing

We have made the following preprocessing to the data to make the data suitable for producing the required results

**Null value Handling**

Two types of null values are present:
* Trailing null values - We have removed them directly from the dataset
* Null values in particular fields - These values are handled by considering some properties

**Converting Categorical values**
* We need to convert the `swm` field and `city_type` field categorical values to numerical values
* This is done by making a dictionary and then mapping them to the dataset

**Correlation Matrix comparison before the preprocessing and after the preprocessing**

![Correlation Matrix comparison](/Prediction_plot/corr_comp.png)

### **Population Growth Rate Computation**

**Aim** - To predict the growth rate at any consecutive year month or day of the population of any given city using mathematical and statistical approach.

**Technique Used and Reason:**

Technique used are basically a formula based approach and determination of population at a given time period and also making use of available techniques like that of Annuity technique that is been employed at financial institutions in order to predict or assess the pay that a person had to be paying the institution after a given period of time. The main reason that a part of Annuity method was used is because of the following reasons
   
1.	This method produces a promising results that are most probably with a difference in the results to be Plus (or) Minus 0.5 to 3 %
2.	The values that are produced can be checked at a regular intervals and also the fact that it can be assessed for both long period(Years) and a short periods(Days)
3.	Many aspects of this technique can be tailored for a variety of purposes.
4.	The End results that are thus obtained can be much similar to the population rate as most analysis use this formula in assessing the counts in bigger cities like that of Chennai, Bangalore, Mumbai, Etc.

**Other techniques Considered:**

To directly predict the Covid-19 Pandemic by using growth ratio formulas and as well as doubling rate formulas. But the main issue is that the growth rate formula can only be applied to 2 corresponding values like that of first day and the next day and so on. But in this case, the consecutive date and time has not been given yet. Therefore, this method cannot be well utilized over here. 
   
**Formulas Used and Explanation:**

1.	To calculate the growth rate over a period of time(2001 – 2011)(in %)

   * Formula Used:
      * Population Rate over 10 Years = ((Population of 2011 / Population of 2001)/ Population of 2001)*100)

2.	To calculate the growth rate over a period of 1 year(in %)

   * Formula Used:
      * Population Rate of 1 year = Population Rate over 10 Years / 10

3.	To calculate the growth rate for 1 month(in %)

   * Formula Used:
      * Population Rate for 1 month = Population Rate of 1 year / 12

### Hypothesis

**1) Death Rate Hypothesis**

A death rate hypothesis. By using the relation between the female and male population and the covid cases we can arguably find a death rate in the ratio of male and female. This hypothesis can bring a factor that will minimize the difference between the population and the covid cases. This could result as a factor when seen in the correlation matrix.

But this hypothesis fails because :
* There are other factors depending on it that are not present like the deceased rate due to other factors/not covid.
* The disease has not been there long enough to get more data on it. 
* Using categorical data to find a growth rate would result better in providing accurate results.

**2) Monthly Covid cases Hypothesis**

The monthly covid cases was found from the train data, it was highly correlated with the train data but then the feature could not be used in the test data because the monthly covid data calculation required the covid data of the cities in the test data and the test data contains different cities than the train data

### Regression Models
**COVID cases prediction PART 01**

1) Linear Regression: Linear regression is used at the starting to model the relationship between independent and dependent attributes by fitting the linear equation. As Number of independent attributes are more in a given dataset, the model doesn’t fit well.

![Linear Regression PART 01](/Prediction_plot/LR_model.PNG)
  
2) Decision Tree: The given training dataset is multi-dimensional data. The decision tree is used to predict COVID cases with multiple information across various branches. This could be relatively inaccurate and unstable when additional data is given to predict.

![Decision Tree Regression PART 01](/Prediction_plot/D_Tree_model.PNG)

3) Random forest classification: RandomForest classifier aims to overcome the issues of Decision tree algorithm and to obtain accurate results. Since this is an ensembling learning model by constructing a multitude of the decision tree, effective results are achieved. Complexity is more.

![Random Forest Tree Regression PART 01](/Prediction_plot/RandomForest_model.PNG)
                     
4) AdaBoost Regressor: The AdaBoost classifier is chosen to improve accuracy by adjusting the weights iteratively. But Overfitting occurs as the major issue in this case.

![AdaBoost Regression PART 01](/Prediction_plot/AdaBoost_model.PNG)
     
5) Gradient Boosting Model: The Gradient boosting algorithm is chosen to improve accuracy because of powerful ensembling techniques from weaker algorithms. 

![Gradient Boosting Regression PART 01](/Prediction_plot/GradientBoost_model.PNG)

6) MLP Regression: The neural network approach is implemented with Multi-Layer Perceptron. Regularisation is done to avoid the overfitting issue.

![MLP Regression PART 01](/image/MLP_model.PNG)

