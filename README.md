Group 7 report about Titanic incident analyzing

Abstract 
This report was written to create a model capable of predicting whether a traveler survived or not. In the model, Gender, Age and Pclass will be included, and we will use two machine learning method which is K Nearest Neighbor and Logistic regression to predict survival chance. Two model will be compared to each other and to the base to find predicting accuracy. Lastly, we will try to deduce the result that we have.

I.	Introduction

Titanic has always been a disaster when talking about voyage. The incident took place way back on April 15th, 1912, when the Titanic sank during its first voyage after striking an iceberg, resulting in the tragic loss of 1502 passengers and crew out of a total of 2224.This sensational tragedy horrified the international community and led towards action taking by formulating better safety regulations for ships. While it is still controversial about who took responsibility of the incident, we can agree that there are certain characteristics share between survivors. In this report, we try to find out what features will likely make an individual survive in the Titanic incident and perhaps in a disaster.
In this report, we intended to use two kind of classification machine learning method which are KNN and Logistic Regression.

II. Methodology

2.1. Source of data
We will use the provided data which come from Kaggle which is a excel file Train.csv (we also uploaded it on Github). The data was recorded during the incident, and it contains numorous information of 890 passagers on that ship. 
2.2. Variable

2.2.1. Data dictionary
| Cột 1      | Cột 2      | Cột 3      |
|------------|------------|------------|
| Hàng 1     | Dữ liệu 1  | Dữ liệu 2  |
| Hàng 2     | Dữ liệu 3  | Dữ liệu 4  |
| Hàng 3     | Dữ liệu 5  | Dữ liệu 6  |
| Hàng 4     | Dữ liệu 7  | Dữ liệu 8  |
| Hàng 5     | Dữ liệu 9  | Dữ liệu 10 |
| Hàng 6     | Dữ liệu 11 | Dữ liệu 12 |
| Hàng 7     | Dữ liệu 13 | Dữ liệu 14 |
| Hàng 8     | Dữ liệu 15 | Dữ liệu 16 |
| Hàng 9     | Dữ liệu 17 | Dữ liệu 18 |
| Hàng 10    | Dữ liệu 19 | Dữ liệu 20 |
| Hàng 11    | Dữ liệu 21 | Dữ liệu 22 |
<br>
*Note: 
pclass: A proxy for socio-economic status (SES)
1st = Upper
2nd = Middle
3rd = Lower

age: Age is fractional if less than 1. If the age is estimated, is it in the form of xx.5

sibsp: The dataset defines family relations in this way...
Sibling = brother, sister, stepbrother, stepsister
Spouse = husband, wife (mistresses and fiancés were ignored)

parch: The dataset defines family relations in this way...
Parent = mother, father
Child = daughter, son, stepdaughter, stepson
Some children travelled only with a nanny, therefore parch=0 for them.

2.2.2. Variable Selection
There are many variables provided, but in the model, we decide to use four independent variables which is Sex, Age, Pclass, Embarked. For dependent variable, we will use Survived for our model. 
The reason we choose these variables is based on three filters. 
First, we check the null value of each column and it turn out there are 177 rows of Age column, 687 rows of Cabin column and 2 rows of Embarkes columns is missing. While we can ‘fix’ Age and Embarked columns, we do not think that is possible to use a column with approximately 80% missing data like Cabin.
Second is the heatmap that we included. From the chart, we can see that Sibsp has low coefficient, so we did not include it in the model. While Fare has a high coefficient, it also has high coefficient with the Pclass so we will also not gonna use that.
*Note: The reason we choose Pclass instead of Fare is Fare is continuos variable, which is more suitable for the regression task.
Third is we have conducted a test logistic regression model annd perform z test amd the test result suggest that we should not use Parch as it is not statistically significant (at z=0.05)

2.3. Preprocessing data

The data that we receive is not cleaned. There are numerous of null value in the Age column, beside the model can run on str data like what we have in Sex column.
For Age column we decide to fill the null value with mean of all the rows in column as there are around 177 missing rows, around 20% of the data, dropping it might lead to less accuracy of the model in general. While filling null value with mean might not improve the accuracy, more accurate age prediction will involve other machine learning model (like random forest), which might extend our presentation’s time too much. 
For Embarked, there were only 2 missing data, so we decide to drop it. We also turn the type of data into numerical. S/C/Q is converted into 0/1/2
For Sex column, we will convert the male/female into 1/0 as model we use from sckitlearn only take numerical input.

2.4. Data Visualizing
2.4.1. Pie chart about Sex and Survived
This chart was made to compare the percentage of female and male in the survivor.
<br>
![image](https://github.com/user-attachments/assets/c24de14d-1e92-48da-a488-18c2f90a8130)
