## King County (Washington) House Sales Price Prediction Models 
## Table of Contents
* [Introduction to Project](#introduction-to-project)
* [Technologies Used](#technologies-used)
* [Project Explanation through CRISP Methodology](#project-explanation-through-crisp-methodology)                
    * [1.Business Understanding/Questions](#1business-understandingquestions)      
    * [2.Data Understanding](#2data-understanding)      
    * [3.Data Preparation/Exploratory Data Analysis](#3data-preparationexploratory-data-analysis)        
    * [4.Data Modeling/Price Prediction Models](#4data-modelingprice-prediction-models)     
    * [5.Evaluation](#5evaluation)     
    * [6.Deployment/Feedback](#6deploymentfeedback)
* [Conclusion](#conclusion)  

## Introduction to Project 
This project was completed in one of the courses under IBM certified data science program. 

The dataset was acquired through kaggle and it was provided by King County Washington. It includes homes sold between May 2014 and May 2015. The goal of the project is to predict the price of housing for 2016 in King County, based on the variables provided in the dataset.  

***What intrigued my interest in this project?***              

The model, built at the end, will accept some variables or house features as input and will give us back the estimated price. It could help prospective homeowners, investors, developers and other real estate market agents. 
 
Although, I was very much engaged during the exploratory analysis and modeling part, I was simultaneously aware of the fact that the data is not very new and probably will not have much impact. But I also knew that it was part of the learning process.

Side note: I also had to complete and submit the project if i wanted the course certificate; so another motivation 🤐.  
***

[(Back to top)](#table-of-contents)  

## Technologies Used  
A list of technologies used within the project:
* Python
* Pandas
* Numpy
* Matplotlib
* Seaborn
* StandardScaler
* Ridge Regression
* Scikit-Learn
* Linear Regression
* Polynomial Features
* Pipeline
* train_test_split, cross_val_score
* r2_score, mean_absolute_error, mean_squared_error
***

[(Back to top)](#table-of-contents)  

## Project Explanation through CRISP Methodology
Cross Industry Standard Process for Data Mining (CRISP-DM) is a process, a methodology, or a framework developed by IBM. A data science team, whenever embarking on a new project, can implement this method for better results and ultimately successful decision-making at the end of the project. 

***Why did i choose this methodology?***

Although it is not the only model out there, but i actually believe that it is the best. It gives you a path and understanding of your tasks beforehand. 

So let's dive into the steps but with out project explanation in mind. 

### 1.Business Understanding/Questions 
This phase could be summed as in the following questions:    
* **What do i want to accomplish?** 
* **What are the questions, i want to find answers to?**
* **What problem do i want to solve? What is my end goal?**
* **How exactly would i do it? What is my project plan**         

The ***objectives*** are to find patterns and discover relationships between different house features and our target variable, price.                                 
* What house features affect the price?
* What house features significantly influence the price?
* What features are the potential predictors of house price?          

 The ultimate ***goal*** of the project is to predict house prices in King county by developing a prediction model. The model will accept some variables as input and will give us back the estimated price. It could help prospective homeowners, investors, developers and other real estate market agents.                                   
 
Now we have well-defined problem and we know what we want to solve. But where is the data? Let me answer it in the next phase.                      

[(Back to top)](#table-of-contents)  

### 2.Data Understanding 
**Data Set:**                  
The dataset can be found here.<nav><a href="https://www.kaggle.com/datasets/harlfoxem/housesalesprediction?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-wwwcourseraorg-SkillsNetworkCoursesIBMDeveloperSkillsNetworkDA0101ENSkillsNetwork20235326-2022-01-01&select=kc_house_data.csv"> House sales in King County, USA </a>                  

The Data Set before cleaning has 21613 entries with 22 columns.           

**Key Features of the Data Set:**      
![alt text](https://github.com/WaheedAhmad-DS/King-County-Washington-House-Sales-Prediction-Model/blob/main/Images/DF.png)
 
* **id -** Unique ID for each house sold.

* **date -** Date when the house was sold.

* **price -** Price of each house sold.

* **bedrooms -** Number of bedrooms.

* **bathrooms -** Number of bathrooms, where .5 accounts for a room with a toilet but no shower.

* **sqft_living -** Square footage of the interior living space of the house.

* **sqft_lot -** Square footage of the land space of the house.

* **floors -** Number of floors in the house.

* **waterfront -** Whether the house is facing a lake or a river or any kind of waterfront.

* **view -** An index from 0 to 4 of how good the view of the property is. 

* **condition -** An index from 1 to 5 on the condition of the house.

* **grade -** An index from 1 to 13, where 1-3 falls short of building construction and design, 7 has an average level of construction and design, and 11-13 have a high quality level of construction and design.

* **sqft_above -** The square footage of the interior housing space that is above ground level.

* **sqft_basement -** The square footage of the interior housing space that is below ground level.

* **yr_built -** The year the house was initially built.

* **yr_renovated -** The year in which house was last renovated.

* **zipcode -** What zipcode area the house is in.

* **lat -** Lattitude

* **long -** Longitude

* **sqft_living15 -** The square footage of interior housing living space for the nearest 15 neighbors. 

* **sqft_lot15 -** The square footage of the land lots of the nearest 15 neighbors.                     

[(Back to top)](#table-of-contents)  

### 3.Data Preparation/Exploratory Data Analysis  
**Data Cleaning:**
1) First, 'Unnamed 0' was dropped.                       
2) 'bedrooms' and 'bathrooms' had missing values which were replaced with mean.                                                      
3) Data types were coherent with their values.                             
4) Duplicates were not present.                                      

[(Back to top)](#table-of-contents)  

#### Exploratory Analysis:                          

**Correlation between price and other features.**  

Through correlation matrix we can identify variables or features that have significant linear relationship (either positive or negative) with price and those who don’t have any relationship. We can also see the features that are highly correlated with each other that is multicollinearity. 

  ![alt text](https://github.com/WaheedAhmad-DS/King-County-Washington-House-Sales-Prediction-Model/blob/main/Images/Correlation%20Matrix.png)   
  
* ***Price has a high positive correlation with sqft_living, grade, and sqft_above.*** 

* ***Price has moderate positive correlation with bathrooms, and sqft_living15.*** 

* ***Price has low positive correlation with bedrooms, floors, sqft_basement, view and latitude.***

* ***Price shows non-significant relationship with sqft_lot, yr_built, and longitude.***  
                       
Let's see the relationship of "sqft_living", "sqft_above", "grade", "sqft_living15", "bathrooms" with our target variable 'price' through ***correlation table.*** 

![alt text](https://github.com/WaheedAhmad-DS/King-County-Washington-House-Sales-Prediction-Model/blob/main/Images/Correlation%20of%20price.png)         

* This table corroborates the above points deducted from correlation matrix. 

Now, let's see it through regression plots. 

[(Back to top)](#table-of-contents)

**Regression plots.**  
 ![alt text](https://github.com/WaheedAhmad-DS/King-County-Washington-House-Sales-Prediction-Model/blob/main/Images/sqft-living.png)       
 ![alt text](https://github.com/WaheedAhmad-DS/King-County-Washington-House-Sales-Prediction-Model/blob/main/Images/sqft_above.png)   
 ![alt text](https://github.com/WaheedAhmad-DS/King-County-Washington-House-Sales-Prediction-Model/blob/main/Images/grade.png)   
 ![alt text](https://github.com/WaheedAhmad-DS/King-County-Washington-House-Sales-Prediction-Model/blob/main/Images/sqft-living-15.png)   
 ![alt text](https://github.com/WaheedAhmad-DS/King-County-Washington-House-Sales-Prediction-Model/blob/main/Images/bathrooms.png)      

[(Back to top)](#table-of-contents)

**Waterfront and price.**      

![alt text](https://github.com/WaheedAhmad-DS/King-County-Washington-House-Sales-Prediction-Model/blob/main/Images/waterfront.png)

* ***Houses with waterfront are associated with high price compared to houses without waterfront.*** 

[(Back to top)](#table-of-contents)  

                                                
### 4.Data Modeling/Price Prediction Models  
Let's train a model which, when given with some specifications, will give us the estimated price of house. Four models were built; Linear Regression, Multiple linear regression, Polynomial regression and pipeline, and Ridge regression.               

The modeling phase can be summarized in the following steps:                        
* **Model Selection:** It involves different ML algorithms. I tried four different models.                         
* **Test Design:** Model test design was designed by splitting the data into training, test, validation sets, and cross-validation.                                
* **Model Development:** The model was fitted using the data we cleaned. 
* **Model Assessment:**  Models were assessed using various statistical techniques.                                              

**1) Linear Regression**    

A sqft_living has the highest positive correlation with price, we will built the linear model based on sqft_living. The cod snippet is below: 

```
lm=LinearRegression()
X=df[['sqft_living']]
Y=df[['price']]
lm.fit(X,Y) 
```
```
lm.intercept_ 
       
       array([-43580.74309447]) 
lm.coef_             

       array([[280.6235679]]) 
```

* The linear model comes out to be  ***price=-43580.74309447+ 280.6235679*sqft_living***. This is called slope-intercept form in mathematical terms. 

**2) Multiple Linear regression**   

```
Z=df[["floors", "waterfront", "lat", "bedrooms", "sqft_basement", "view", "bathrooms", "sqft_living15",
      "sqft_above", "grade", "sqft_living"]]
A=df[['price']]
lm.fit(Z, A)
print (lm.intercept_)
print (lm.coef_)  
```

```
[-32382535.85823347]
[[-2.98936449e+04  6.01930234e+05  6.72855361e+05 -2.59783985e+04
  -4.73564581e+14  6.70908533e+04 -3.26565588e+03  4.54356111e+00
  -4.73564581e+14  8.20151586e+04  4.73564581e+14]]
```



**2) Polynomial Features and pipeline building**  

**3) Ridge Regression**                                                                                   


[(Back to top)](#table-of-contents)  

### 5.Evaluation
**Technical Evaluation**                        

Technical evaluations of the models have been done above where we found the accuracy measurements regarding all the four models.                         

**Non-technical Evaluation**                                                                                               

***This is of utmost importance. It can be described as below.***                                      

* **Evaluating Results:** This involves evaluating the model concerning the business indicator. The data mining results should be rigorously assessed, probably in a controlled laboratory setting. Why? To gain confidence that they are reliable before moving to deployment phase.                                   

* **Review Process:** From this phase we can go back to First phase and start the overall process again for better results and decision-making. What if we need more data? May be, all phases were not executed as they should have been, etc.                                                                                                                      

*  **Next Steps:** The model may well be ready for deployment or may be iteration of the CRISP-DM methodology is required. Depending on the previous phases different decisions could be taken.                                                     

**Evaluation of our project**                                      

Technical evaluation of our Ridge regression model is near to accurate. But evaluation in the actual business context may reveal some failures. Also the data is not very new, although same techniques can be applied to newer datasets.                    

[(Back to top)](#table-of-contents)  

### 6.Deployment/Feedback                                                           

* It involves implementing a predictive model in some information system or business process.                                 

* In our house price prediction example, price-predicting model could be integrated with the business process. It can be deployed on website only after analysis with newer version of data. Visitors could enter the features of the house and would get back the estimated price.                                                 

***Note: The process often returns to the first phase of Business Understanding regardless of the success of deployment. A second iteration may produce improved solutions to the problems***                                                             

***

[(Back to top)](#table-of-contents)  

## Conclusion                                                    

* Price increases with increase in Square Feet Living, Square Feet above, Number of Bathrooms and Number of Bedrooms.

* Houses with waterfront are associated with high price compared to houses without waterfront. 

* Price increase with increase in Grade and Condition.

* Price prediction model was developed with more than 75 % accuracy, and the model can be deployed dependig upon the interests. 
  
[(Back to top)](#table-of-contents)  
***
