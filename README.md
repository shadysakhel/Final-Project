# Prediction of Accident Severity
# Introduction
Did you know that on average 3,700 people lose their lives everyday due to road accidents? That is 1.35 million people a year! Not only that, another 50 million people suffer long term disabilities!
Countries all over the world work hard to reduce the number of fatalities and injuries that are caused by road accidents. From bicycle dedicated lanes, speed control, black-point systems to awareness campaigns, all these did help in reducing the number of accidents. Yet, "Road crashes are the leading cause of death in the U.S. for people aged 1-54" as reported by The Association for Safe International Road Travel. In this project, I will attempt to create a model that can predict the severity of an accident given the current weather and road conditions. This model can help warn drivers of the risk they are going to be taking when they decide to drive. In turn, they might change their route or even postpone the commute if its not urgent.

# Business Understanding
Less accidents means less damages on health & property. Tools that can reduce the number of accidents can be of a great value to governments who would want a smooth traffic flow across their cities and protect the wellbeing of their citizens. Also, insurance companies who would be interested in minimizing their losses of repairing properties & covering medical bills. In this project, we will use the data collected by Seattle SPOT Traffic Management Division which contains records of all accidents from 2004 to present to help us predict the severity of accidents that could happen as a result of the current weather and road conditions. The record contains 37 attributes which we will analyze and use to be able to predict the severity of potential accidents with the highest level of accuracy.
# Data Understanding
The dataset we selected has 194,673 rows and 37 different independent attributes. The target variable Y also known as Dependent Variable will be SEVERITY CODE. We will use the relevant attributes from the 37 attributes as our independent variable X. The data set is quite large and we need to get rid of irrelevant columns, rows with missing data which we can’t make an assumption for and also we need to make sure our data set is balanced.
The dependent variable, “SEVERITYCODE”, contains numbers that correspond to different levels of severity caused by an accident. The code that corresponds to the severity of the collision:
•	3—fatality
•	2b—serious injury
•	2—injury
•	1—prop damage
•	0—unknown
At this point we would like to note that the dataset provided by Seattle SPOT Traffic Management Division has data for accidents with “SEVERITYCODE” 1 and 2 only.
The independent variables are many and we list below the most important ones:
•	PERSONCOUNT: The total number of people involved in the collision helps identify severity involved
•	PEDCOUNT: The number of pedestrians involved in the collision helps identify severity involved
•	PEDCYLCOUNT: The number of bicycles involved in the collision helps identify severity involved
•	VEHCOUNT: The number of vehicles involved in the collision identify severity involved
•	INCDATE  : The date of the incident.  
•	ADDRTYPE: Collision address type: Alley, Block, Intersection
•	COLLISIONTYPE: Collision Type
•	JUNCTIONTYPE: Category of junction at which collision took place helps identify where most collisions occur
•	INATTENTIONIND: Whether or not collision was due to inattention.
•	UNDERINFL: Whether or not a driver involved was under the influence of drugs or alcohol. 
•	LOCATION: Description of the general location of the collision
•	WEATHER: A description of the weather conditions during the time of the collision
•	ROADCOND: The condition of the road during the collision
•	LIGHTCOND: The light conditions during the collision
•	SPEEDING: Whether speeding was a factor in the collision (Y/N)
Attributes like "INATTENTIONIND", "UNDERINFL" & "SPEEDING" cause noise in our data as we are interested in the effect of the weather and road condition on the severity of the accident. We know that these attributes do contribute to the severity of the accident but for the purpose of analyzing the weather and road condition only we will drop incidents that had been affected by "INATTENTIONIND", "UNDERINFL" & "SPEEDING".
# Loading the Data

I will be using JupyterLab on Skills Network Lab for this project. The language of the code will be Python.
 
# Cleaning the Data
As part of cleaning the data, the following shall be done:
1)	UNDERINFL seem to be a mix of Y & N and Boolean Values 0 & 1. Here We change all to Boolean
2)	Some data is set to "unkown" which we will change to Nan (Python's default missing value marker)
3)	We will need month and year in separate columns to perform some analysis on the data later
4)	Change "INCDATES" to indicate either weekday or weekend
5)	Dealing with missing Data (Drop Incidents with missing Data)
6)	Drop incidents caused by inattention as this will cause noise to the relation of accidents with weather
7)	Drop incidents caused by driving under the influence of alcohol or drugs as this will cause noise to the relation of accidents with weather
8)	Drop incidents that have a missing information whether the driver was driving under the influence
9)	Drop incidents related to speeding as this will cause noise to the relation of accidents with weather
10)	Drop incidents that do not have WEATHER, ROADCOND, LIGHTCOND, ADDRTYPE or COLLISIONTYP indicated
11)	 We will not need the attributes INATTENTIONIND, UNDERINFL & SPEEDING. So we will drop them
12)	Convert Categorical features to numerical value
 
The numerical codes of the categorical variables are defines as the below dictonaries:
 

# Data Visualization 
The graph below shows the change in number of accidents per year from 2004 till 2020 (2020 Data is only till May)
 
The graph below shows the change in number of accidents over months of the year. Since 2020 data is not for a complete year we will exclude it in this part of the analysis
 
The graph below shows the change in number of accidents over the days of the week
 
# Balancing the Data
 
As you can see, our data has more incidents of severity code 1 than code 2, we need to balance the data set.
 
# Train-Test Split
 
Next, we will have to normalize the data
 
# Methodology
At this point we are ready to begin testing different classification algorithms. Our project is a typical classification problem as we attempt to learn the relationship between a set of feature variables and a target variable of interest. The aim is to find the best classification algorithm that will be able to predict the "SEVERITYCODE" of a certain incident given a defined X attributes with the highest accuracy. We will test k-nearest neighbor, Decision Tree, Support Vector Machine & Logistic Regression.
K-Nearest Neighbors
In the K-Nearest Neighbors, we need to analyze which value ok K gives us the best accuracy. We will perform the analysis on a range ok K values from 1 to 25 and see how the accuracy changes.
 
Plotting the accuracy vs the K values
 
We can see that the best accuracy is with a K value of 21. Therefore, we will build the model using K value of 21
 
KNN Model Evaluation:
 

# Decision Tree
 
Decision Tree Model Evaluation:
 
# Support Vector Machine
 
Support Vector Machine Model Evaluation:
 
# Logistic Regression
Since our target variable is of a binary nature, it would be perfect for logistic regression.
 
Logistic Regression Model Evaluation:
 
# Models Comparison
 

# Discussion & Conclusion
Based on the evaluation metric results listed above, we can say that all 4 algorithms have resulted in almost a similar result. The best accuracy is with the Decision Tree algorithm which has an accuracy percentage of about 69%. Although, we can confidently say that our model with the decision tree can predict whether an accident will result in a severity code 1 or 2, the accuracy is not that high. Our model seems to be underfitted. Since we have many attributes which contribute to the severity of the accident, we can say that collecting more data of more accidents will help increase the accuracy of the model. We have lost quite a number of data in the cleaning process which was mainly due to some attributes being missed in the collection of the data.

