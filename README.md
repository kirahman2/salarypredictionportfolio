![alt text](https://github.com/kirahman2/salarypredictionportfolio/blob/master/Images/salary-image.png)
# How Can We Predict Salary Based on Employee Job Descriptions?

## Introduction
For this salary prediction project I examined different attributes of employee information to predict their salary

## Data
The data is part of an existing data set that includes employee information. The features of the dataset include job id, company id, job type, degree, major, industry, years experience and miles the employee lives from from the metropolitan city. The actual size of the dataset is 1,000,000 rows. 

## Preprocessing
For the data cleaning process, I followed the steps listed below.
* Removed 5 rows where salary equaled 0, which indicated missing values 
* Removed 7117 rows for salaries more than 220 since this goes beyond the upper 75% percentile (outlier removal)
* Records with a degree and major listed as "None" were replaced with "Missing"
* Categorical variables were imputed which included company id, job type, degree, major and industry

## Exploratory Data Analysis
Prior to the exploratory phase I hypothesized that a higher level education equated with a higher salary. To test this theory, I looked at a boxplot of salary compared against degree. It turns out that someone with a PhD earns only slightly more than someone with a masters and bachelors.

![alt text](https://github.com/kirahman2/salarypredictionportfolio/blob/master/Images/salary_degree.png)

I was then curious about the different industries and hypothesized that the web industry would be the highest earning. It turns out Finance and Oil are the highest earning industries. 

![alt text](https://github.com/kirahman2/salarypredictionportfolio/blob/master/Images/salary_industry.png)

After examining the results of each feature, I noticed Company Id was divided into 63 groups. After diving deeper and examining each feature against company Id, I did not find signs of grouping. I did however notice variation in the average salary for each Company Id group. 

![alt text](https://github.com/kirahman2/salarypredictionportfolio/blob/master/Images/salary_compid.png)

Looking a bit deeper, within each company id group, there were variations in earnings by job title, degree, major and industry. For example,

![alt text](https://github.com/kirahman2/salarypredictionportfolio/blob/master/Images/salary_comp19_.png)
![alt text](https://github.com/kirahman2/salarypredictionportfolio/blob/master/Images/salary_comp37_.png)

The variations in company salary were important signals to consider. 

