### Virgin Money Employee Churn-Analysis

Analysis of why Male "Band E" Employees working in customer serivce are leaving Virgin Money.


## Introduction 

The raw data for this analysis has been provided by Virgin Money and includes data on all Employee Hires, Leavers, Grade and Position Changes since 2013. 

The Raw data has been stored in MS-SQL. SQL Server has been used to create a Datawarehouse, transforming the data for analytical purposes. This transformed data has then been analysed using Python, with packages such as "SKLearn" and "Plotly" to visualise the data and to provide machine learning functionality that will predict the liklihood of employees of leaving. Indicating who is "High risk". Feature analysis has also been used to 


### Raw Data

Raw data received from Virgin Money. Database Data tabulating all leavers, hires since 2013 and any Grade or Position Changes that any employee underwent. 

## Employ_hires_All_Time 

# Overview (Column Info):
* Payroll Number 
* Gender
* Age
* Hire Date
* Position Reference
* Position Title
* Grade
* User Assignment Status
* Employment Category
* Function 
* Division
* Department
* Section 
* Team 
* Location Name 
* Location Postal Code

# Profile
* Records - 2011 
* Distinct Employees - 1955
* Males 			- 899 (44.70%)
* Females			- 1112 (55.30%)

* Band E Employees 	- 1121 (55.74%)
* Band E Males 		- 377 (33.63.94%)
* Band E Females 		- 744 (66.90%)

* Hire Dates from  2013-12-02 to 2018-01-04

# Comments

## Leavers_all_time 

# Overview (Column Info):
* Payroll Number 
* Gender
* Age
* Hire Date
* Termination Date
* Termination Reason
* Position Reference
* Position Title
* Grade
* User Assignment Status
* Employment Category
* Function 
* Division
* Department
* Section 
* Team 
* Location Name 
* Location Postal Code

# Profile
* Records - 1568 
* Distinct Employees - 1538
* Males 			- 716 (45.66%)
* Females			- 852 (54.33%)

* Band E Employees 	- 803 (51.21%)
* Band E Males 		- 268 (33.37%)
* Band E Females 		- 535 (66.62%)

* Hire Dates from 1971-07-19 to 2017-11-07
* Termindation Dates from 2013-12-06 t0 2018-02-08

# Comments/Issues

## Position Changes All Time:

Data on an employees position change within the company. 
Position changes can constitute a grade change, or the new position can be of the same grade.

# Overview (Column Info):
* Employee/Contingent Number
* Gender
* Age
* Previous Position Title
* Previous Grade Name
* Previous Employment Category
* New Grade Name
* New Employment Category
* Assignment Start Date
* Previous Assignment Status
* Previous Function
* Previous  Divsion (P)
* Previous Department (P)
* Previous Section (P)
* Previous Team (P) 
* New Assignment Status
* New Function
* New Divsion (P)
* New Department (P)
* New Section (P)
* New Team (P)

# Profile:
* Records - 2955  
* Distinct Employees - 1881 

* Assignment Start Date from 2013-12-01 to 2018-01-22

# Comments/Issues 

## Grade Change All Time:

# Comments
All Position Changes that result in a grade changes.

Grades in the Position and and Grade Change tables are more granular than all other tables. Breaking down into sub-grades i.e. E-E2 and D-D1BC.

A position is not always indicative of the grade the employee has. 
For example 3 'Assistant Management Accountant's' have the Grades: D-D2, D-D3FI and D-D4.

It has been assumed that the numerical component of the grade change is in descending rank i.e E-E1 > E-E2.
It is unclear what consitutes a 'Organisational Change'

# Overview (Column Info):

* EmployeeNumber
* Gender
* Age
* Position Title (Previous)
* New Position Title
* Employment Category
* Grade Name (Previous)
* Grade Name
* Effective Start Date (P)
* Organsational Change (P)
* Function (Previous)
* Division (Previous)(P)
* Department (Previous)(P)
* Section (Previous)(P)
* Team (Previous) (P) 
* Function(P)
* Division(P)
* Deparment(P)
* Section (P)
* Team (P)

# Profile: 

# Issues: 

### Transformed Tables for Analsis

## Introduction 

Various techniques were used to create 4 tables upon which analysis could be performed from the Raw data provided. These were Employee Profiles, Leaver Profiles, Location Profiles and Appraisal Goal Analysis. 

## Store Profiles
T



