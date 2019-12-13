![alt text](https://github.com/kirahman2/salarypredictionportfolio/blob/master/Images/salary-image.png)
# How Can We Predict Salary Based on Employee Job Descriptions?

## Introduction
For this salary prediction project I am examining different attributes of employee information to predict their salary. 

What does this look like? 


## Data
The data is part of an existing data set that includes employee information. The features of the dataset used include job id, company id, job type, degree, major, industry, years experience and miles the employee lives from from the metropolitan city. The actual size of the dataset is 1,000,000 rows. 

## Preprocessing
For the data cleaning process, I followed the steps listed below.
* Removed 5 rows who's salaries were 0, which indicates missing values 
* Removed 7117 rows with salary more than 220 since this goes beyond the upper 75% percentile
* Records with a degree and major listed as "None" were replaced with "Missing"
* Imputed categorical variables including company id, job type, degree, major and industry

## Exploratory Data Analysis
Prior to the exploratory phase I hypothesized that a higher level education equated with a higher salary. To test this theory, I looked at a boxplot of salary compared against degree. 

IMAGE degree

It turns out that someone with a PhD earns only slightly more than someone with a masters and bachelors. (include actual average pay). 

I then wondered about industries and hypothesized that the web industry would be the highest earning. On second thought, after seeing the results, it makes sense that Oil and Finance would be the highest earning industries. 

IMAGE industry

After examining the results of each feature, I noticed Company Id was divided into 63 groups. After diving deeper and examining each feature against company Id, I did not find any signs of grouping. I did however notice variation in the average salary for each Company Id group. 

IMAGE salary_compid

Looking a bit deeper, within each company id group, there were variations in earnings by job title, degree, major and industry. For example,

IMAGE comp19 and 37

The variations in company salary were important signals to consider. 

