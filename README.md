### Virgin Money Employee Churn-Analysis

Analysis of why Male "Band E" Employees working in customer serivce are leaving Virgin Money.


## Introduction 

The raw data for this analysis has been provided by Virgin Money and includes data on all Employee Hires, Leavers, Grade and Position Changes since 2013. 

The Raw data has been stored in MS-SQL. SQL Server has been used to create a Datawarehouse, transforming the data for analytical purposes. This transformed data has then been analysed using Python, with packages such as "SKLearn" and "Plotly" to visualise the data and to provide machine learning functionality that will predict the liklihood of employees of leaving. Indicating who is "High risk". Feature analysis has also been used to 


### Raw Data

Raw data received from Virgin Money. Database Data tabulating all leavers, hires since 2013 and any Grade or Position Changes that any employee underwent. 

## General Issues with Raw Data


There are discrepencies through the data for the Ages of staff. If a staff member has left (present in Employee_Leavers_all_time) then there age is displayed as their age upon hire, else their age is the employees current age ie: 
Employee Number	Gender	age	grade	Hire Date
0006847		Female	15	Band E	1971-07-19 00:00:00.000
0008068		Female	63	Band E	1972-10-29 00:00:00.000

Employee 0008068 cannot have been 63 when hired into company and still be in employment.
Likewise Employee 0006847 cannot have been hired in 1971 and upon leaving be 15.

There also appears to be issues with location information for the individual employees. 2173 (34.16%)of records are stated to be based in Gosforth and 1207 (18.97%) in Jubilee House. Jubilee House is in Gosforth and is the HQ for Virgin Money, making it likely that these are the same office locations. 

That would mean 53.13% of all staff are based at HQ, would does not seem plausible. 

The Assumption that has been used is that all employees based in branch locations prior to a certain date have been later 'Re-assigned' to Gosforth and Jubilee house. Reasons could be due to the Virgin Money aquirement of 'Northern Rock' or due to some other change of the data warehouse the Raw data is derived from. 

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

# Introduction
Raw tables: 
* Hires 
* Leavers
* Grade Change 
* Position Chance 

# Overview (Column Info)
* Locations
* LocationID
* Total Staff
* Males
* Females
* Percentage Female
* Band C
* Band D
* Band E
* Staff Left 2012
* Staff Hired 2012
* Staff Left 2013
* Staff Hired 2013
* Staff Left 2014
* Staff Hired 2014
* Staff Left 2015
* Staff Hired 2015
* Staff Left 2016
* Staff Hired 2016
* Staff Left 2017
* Staff Hired 2017

# Profile 
* 90 Distinct Locations

# Comments 

Raw data is not correct for some locations i.e there are several different entries for Edinburgh locations. This makes it difficult to distinguish between office locations such as in Norwich and the branch location also there. 

Staff location within Jubilee house is sub-divided in to building and floor location in the raw data so this has been grouped together.

The parameters the stores have been profile by is the Total number of staff, the number of male and female employees and the percentage of staff that are Female. The locations are also measured by the number of band C,D,E Employees. 
As the highest grade a store manager can be is Band D, no Band C or other upper management staff members are found in any of the bank branches. All locations with Band C staff are in regional offices  such as the ones located in Chester, Edinburgh, Gosforth, London and Norwich. 

The profiling of a stores "make-up" was attempted inorder to see if there are particualr attributes or group of attributes that could lead to a high rate of Band-E Males leaving the company, some indicators that were proposed were geography, the gender percentage (is a male employee more likely to leave if there are fewer male employees already in that location). 
However due to the staff location issues mentioned previoulsy (53% of staff "in" Gosforth) a true understanding of who is working in each store could not be created, this is evident from the fact that 43 of the store locations have fewer than 9 employees, which would seem unlikely. 

It should be noted that this "total" is total number of staff who have EVER worked there, not the value currently working in that location. 


## Leavers Profiles: 

# Introduction

# Overview (Column Info)

# Profile 

# Comments 

# Issues 

## Leavers Profiles: 

# Introduction

# Overview (Column Info)

# Profile 

# Comments 

# Issues 

## All Employee Profiles: 

# Introduction

# Overview (Column Info)

# Profile 

# Comments 

# Issues 

## Goal Analysis

### Analysis 

## Python 

## Machine Learning 

## Neo4J




