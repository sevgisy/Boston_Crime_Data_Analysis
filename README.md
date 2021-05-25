# Boston_Crime_Data_Analysis
## Content
1. [Guiding Questions](#1)
2. [Gathering Data](#2)
   1. [Data Wrangling](#3)
3. [Exploratory Data Analysis](#4)
4. [Modelling](#5)
5. [Conclusion](#6) 
6. [References](#7)
<a id = "1"></a><br>
## Guiding Questions
In the first step, I determined what I curious about Boston Crime Data in light of the above-mentioned information, and I wrote these down:

1. How has crime changed over the years?
1. What can you say about the distribution of different offenses over the city?
1. Is it possible to predict crime type will be committed?

I will use python libraries within the Jupyter notebook environment for Investigation these questions. The main software libraries I’ll be importing are Pandas, NumPy for data wrangling and Matplotlib, Plotly for data visualization.
<a id = "2"></a><br>
## Gathering Data

_Crime incident reports are provided by Boston Police Department (BPD) to document the initial details surrounding an incident to which BPD officers respond_.[²](https://data.boston.gov/dataset/crime-incident-reports-august-2015-to-date-source-new-system/resource/12cb3883-56f5-47de-afa5-3b1cf61b257b?inner_span=True) Boston crime data distributed by Analyze Boston is publicly available. </n>

Data in the Boston crime can be reachable from Analyze Boston's [web data portal](https://data.boston.gov/dataset/crime-incident-reports-august-2015-to-date-source-new-system/resource/12cb3883-56f5-47de-afa5-3b1cf61b257b?inner_span=True). According to [Open Data Commons Public Domain Dedication and Licence](http://opendefinition.org/licenses/odc-pddl/). The data set allows you to freely share, modify, and use this work for any purpose and without any restrictions.</n>

The Boston crime data domain disseminates numbers of different types of offences by Boston's districts. The current dissemination covers the period from August 2015– December 2020. It includes areas of all the countries and territories of the world. (In 2019: 190 countries and 37 other territorial entities) The data covers records from the recent crime incident report system between 2015 and 2020. The format is a comma-separated value (CSV) file, has a tabular format and 93.4 megabytes. It includes 536k rows and 17 columns.</n> 
While the incident number, offence code and date information do not have any missing information, the other features have some missing values. Additionally, the source of data gave some detailed information about each feature. These are shown below the table. As far as I understand from the table, this CSV file was converted from an SQL database. Also, there is no information about location variables.

| Field Name| Data Type| Required| Description |
| --------- | ---------|---------|------------ |
| incident_num| varchar(20)|Not null|Internal BPD report number
| offence_code|varchar(25)|null|Numerical code of offence description 
| offence_code_group_description| varchar(80)|null|Internal categorization of offence_description
|Offence_Description|varchar(80)|null|Primary descriptor of incident
|district|varchar(10)|null|What district the crime was reported in
|reporting_area|varchar(10)|null|RA number associated with the where the crime was reported from.
|shooting|char(1)|null|Indicated a shooting took place
|occurred_on|datatime2(7)|null|Earliest date and time the incident cloud have taken place
|UCR_Part|varchar(25)|null|Universal Crime Reporting Part number(1,2,3)
|street|varchar(50)|null| Street name the incident took place

<a id = "3"></a><br>
### Data Wrangling

In this project only a small amount of cleaning and wrangling was required to obtain my visualizations. My cleaning and wrangling activities included:

1. Data columns rename:<br>
   I changed all columns' names as low letter for standardization.

1. Deleting of unwanted columns:<br>
   From the above descriptive statistics table, and also the above explanation of each variables, I decided to not use below variables:<br>
   incident_number: Because it is a report number, it also shown the actual crime count number. However, some cases includes more than one type offence, this number is duplicated for some cases. As you can see the below table, the case that included the highest different offence types is 20. I think that this was really interesting information. However in our analysis, I will try to make a prediction, so this column does not give me valuable information.<br>
   offence_code & offence_description: These columns include same information about offence description. Offence code just a number of offence description. Because the data set has internal categorization if offence description, I will use offence code group column.<br>
   reporting_area: Because already have district information, I will use this instead of RA number.<br>
   occured_on_date: The date has already split as year, month, day of week, hour so I will use these.<br>
   location: The date has already provided lat and long values, so I will not use this column also.<br>
   
1. Deleting of unwanted rows:<br>
   To compare each full year, and to solve unbalanced data problem in yearly base, I will delete 2020 and 2015 rows.<br>
   I wanted to analyse each district, but I realized that District has a 'External' value, I will also delete these rows.<br>
   Even if some lat and long information is not null, they showed different location than Boston, so I limited according to true Boston's coordinates.<br>
    
1. Null values:<br>
   Export cleaned data to create SQL file.
   
<a id = "4"></a><br>   
# Exploratory Data Analysis 

In this section, I will try to find answers to my first and second guiding questions. So, based on these questions, I will investigate when and where crime mostly occurred. Additionally, I am planning to make some visualizations to understand the relationships between variables.

<a id = "5"></a><br>   
# Modelling
 -Decision Tree<br>
 -Random Forest<br>
 -Neural Networks<br>
 
 <a id = "6"></a><br>
 #Conclusion
 You can find details and codes of the project in the .ipynb file. This project has come across an unbalanced data problem, so the results of machine learning algorithms have not enough to success. So, I will update this project while I learn new technics for solving this problem.

