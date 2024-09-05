# Remote Healthcare Monitoring

## Problem Statement
Can we build a model that can detect health alerts for continuous remote monitoring?

## Background
Dementia is a progressive condition that affects cognitive and functional abilities. There is a need for reliable and continuous health monitoring of People Living with Dementia (PLWD) to improve their quality of life and support their independent living. Healthcare services often focus on addressing and treating already established health conditions that affect PLWD. Managing these conditions continuously can inform better decision-making earlier for higher-quality care management for PLWD. Via machine learning and analytical models we can detect and predict adverse health events affecting the well-being of PLWD. 
The motivation behind it is to showcase analytical skills behind this dataset, including:
	-Exploratory data analysis
	-Pre-processing data
	-Building an alert detection model

## Goal

Using Machine Learning methods, we wish to detect system alerts across different health variables, across multiple patients that suffer from dementia.

## TIHM-Dataset

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.7622128.svg)](https://doi.org/10.5281/zenodo.7622128) 
<br/>

The data utilised was extracted from this article: TIHM: An open dataset for remote healthcare monitoring in dementia.
The dataset is available on its corresponding [Zenodo repository](https://zenodo.org/record/7622128).
The full description of this dataset is published in Nature Scientific Data: [paper](https://doi.org/10.1038/s41597-023-02519-y)

The data was collected from homes of 56 PLWD and associated with events and clinical observations (daily activity, physiological monitoring, and labels for health-related conditions). 
The study recorded an average of 50 days of data per participant, totalling 2803 days.

## Results 

We were able to replicate the findings of the article, where the linear regression model proved to be a better classification model of Agitation.
Furthermore, the SHAP values also indicate that 'Activity' data is more relevant than 'Physiological' data for that prediction.

## Risks and Assumptions
The results of this study depend greatly on certain assumptions. The response variable does not apply to all cases on the dataset (originally a different type of study), so there is a loss of data. Furthermore, the data is a cohort of patients from the UK, which must be considered when looking at populations from other areas.


## Data Dictionaries

The dataset is organised in five separate tables stored as separate CSV files, including, Activity, Sleep, Physiology, Labels and Demographics. Data can be cross-referenced across the files. 

### Activity

|               | Value Type        | Number of Values | Description                                     |
|---------------|-------------------|------------------|-------------------------------------------------|
| patient_id    | CategoricalDtype  | 56               | hash code                                       |
| location_name | CategoricalDtype  | 8               | Hallway,Lounge,Fridge Door,Bedroom,Kitchen,etc.       |
| date    | dtype[datetime64] | N/A              | from 2019-04-01 to 2019-06-30 |

### Labels

|            | Value Type        | Number of Values | Description                                         |
|------------|-------------------|------------------|-----------------------------------------------------|
| patient_id | CategoricalDtype  | 49               | hash code                                           |
| date | dtype[datetime64] | N/A              | from 2019-04-04  to 2019-06-30     |
| type       | CategoricalDtype  | 6                | Agitation,Body temperature,Weight,etc. |


### Physiology

|             | Value Type        | Number of Values | Description                                                                 |
|-------------|-------------------|------------------|-----------------------------------------------------------------------------|
| patient_id  | CategoricalDtype  | 55               | hash code                                                                   |
| date  | dtype[datetime64] | N/A              | from 2019-04-01 to 2019-06-30                             |
| device_type | CategoricalDtype  | 8                | Skin Temperature,Diastolic blood pressure,Heart rate,O/E - muscle mass,etc. |
| value       | dtype[float64]    | N/A              | min: 0.0, max: 211.0                                                        |
| unit        | CategoricalDtype  | 5                | %,kg,mm[Hg],beats/min,etc.                                                  |

### Sleep

|                  | Value Type        | Number of Values | Description                                     |
|------------------|-------------------|------------------|-------------------------------------------------|
| patient_id       | CategoricalDtype  | 17               | hash code                                       |
| date       | dtype[datetime64] | N/A              | from 2019-04-01 to 2019-06-30 |
| state            | CategoricalDtype  | 4                | LIGHT,AWAKE,DEEP,REM                            |
| heart_rate       | dtype[float64]    | N/A              | min: 37.0, max: 107.0                           |
| respiratory_rate | dtype[float64]    | N/A              | min: 8.0, max: 31.0                             |
| snoring          | dtype[bool]      | 2                | True or False                                   |


### Demographics

|               | Value Type        | Number of Values | Description                                     |
|---------------|-------------------|------------------|-------------------------------------------------|
| patient_id    | CategoricalDtype  | 56               | hash code                                       |
| sex | CategoricalDtype  | 2               | Male, Female       |
| age    | CategoricalDtype | 3              | (70, 80],(80, 90],(90, 110] |


