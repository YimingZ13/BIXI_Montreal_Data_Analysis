# BIXI Montreal Bike Usage Data Analysis

## Table of Contents
1. [Introduction](#Introduction)
2. [File Structure](#FileStructure)
3. [Installing](#Installing)
4. [Feature Documentations](#FeatureDocumentations)
5. [Key Results](#KeyResults)
6. [Authors](#Authors)
7. [License](#License)

<a name="Introduction"></a>
## Introduction
In the vibrant and dynamic city of Montreal, where the pulse of urban life intertwines with the spirit of exploration, BIXI bike-sharing has become an integral part of the daily landscape. As the metropolis embraces sustainable and convenient transportation solutions, understanding the nuances of BIXI bike usage becomes paramount for both optimizing operational efficiency and enriching the user experience.

This data analysis project delves into the wealth of information amassed from the usage patterns of BIXI bikes in Montreal. By meticulously dissecting diverse facets of user behavior, trip dynamics, and temporal trends, I aim to unearth actionable insights that can propel BIXI towards greater success. From the geographical popularity of stations to seasonal fluctuations, from member-centric preferences to weekend leisure pursuits, this analysis endeavors to unravel the intricacies that shape the BIXI bike ecosystem.

As we embark on this exploration, the overarching goal is to not only comprehend the current landscape but also to pave the way for strategic enhancements. By deciphering the data intricacies, we seek to provide BIXI with concrete recommendations that align with the diverse needs of Montreal's residents and visitors. Join me on this journey through the data lanes of BIXI bike Montreal, where every data point is a testament to the city's evolving mobility and the potential for sustainable urban progress.

The [original datasets](https://s3.ca-central-1.amazonaws.com/cdn.bixi.com/wp-content/uploads/2023/06/Historique-BIXI-2021.zip), sourced from the BIXI Montreal [Open Data website](https://bixi.com/en/open-data), encapsulates bike usage and station data throughout the year 2021.

<a name="FileStructure"></a>
## File Structure
Each of the following project steps is completed in a separate notebook:
- [Raw Trips Data](https://github.com/YimingZ13/BIXI_Montreal_Data_Analysis/blob/main/2021_donnees_ouvertes.csv): `2021_donnees_ouvertes.csv`
- [Raw Stations Data](https://github.com/YimingZ13/BIXI_Montreal_Data_Analysis/blob/main/2021_stations.csv): `2021_stations.csv`
- [Data Cleaning](https://github.com/YimingZ13/BIXI_Montreal_Data_Analysis/blob/main/BIXI_cleaning.ipynb): `BIXI_cleaning.ipynb`
- [EDA/Business Recommendations](https://github.com/YimingZ13/BIXI_Montreal_Data_Analysis/blob/main/BIXI_EDA.ipynb): `BIXI_EDA.ipynb`

<a name="Installing"></a>
## Installing
There are no special packages needed for this project, most of packages come with the Anaconda distribution of Python 3.

<a name="FeatureDocumentations"></a>
## Feature Documentations
`2021_donnees_ouvertes.csv`:
- `start_date`: Date and time of the start of the trip (yyyy-MM-dd HH:mm:ss.SSSSSS)
- `emplacement_pk_start`: Code of the station where the trip starts
- `end_date`: Date and time of the end of the trip (yyyy-MM-dd HH:mm:ss.SSSSSS)
- `emplacement_pk_end`:  Code of the station where the trip ends
- `duration_sec`: Duration of the trip in seconds
- `is_member`: Memebership status of the trip (1: member, 0: non-member)
  
`2021_stations.csv`:
- `pk`: Station code
- `name`: Name of the station
- `latitude`: Latitude coordinates of the station
- `longitude`: Longitude coordinates of the station

<a name="KeyResults"></a>
## Key Results
- Country Portugal is the most predictive features for the model, as we saw in the EDA, guests who are from Portugal most likely to cancel their bookings
- Guests who made car parking and special requests and specal requests are least likely to cancel
- Longer lead time result in higher cancel chance
- Agent 9 has the lowest success rate of retaining the bookings
- CatBoost is the best performing model yielded 84.24% accuracy, 81.65% recall, 67.71% precision, and 74.03% F1 score on the test set
- After optimizing predicting threshold, the model's precision increased to 68.72%, and recall decreased to 80.36%. The model's ability to accurately predict actual canceled bookings decreased by 62 instances, but it has become significantly more reliable in avoiding misclassifying non-canceled bookings as canceled, with a reduction of 113 such instances. It's a favorable trade-off in performance

<a name="Authors"></a>
## Authors
Yiming Zhao | [LinkedIn](https://www.linkedin.com/in/yiming-zhao13/)

<a name="License"></a>
## License
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

The project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details
