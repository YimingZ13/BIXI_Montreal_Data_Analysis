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
- `ADR`: Average Daily Rate (Calculated by dividing the sum of all lodging transactions by the total number of staying nights)
- `Adults`: Number of adults
- `Agent`: ID of the travel agency that made the booking (If 0.0 was given, it means that the booking was made without one)
- `ArrivalDateDayOfMonth`: Day of the month of the arrival date
- `ArrivalDateMonth`: Month of arrival date with 12 categories: “January” to “December”
- `ArrivalDateWeekNumber`: Week number of the arrival date
- `ArrivalDateYear`: Year of arrival date
- `AssignedRoomType`: Code for the type of room assigned to the booking. Sometimes the assigned room type differs from the reserved room type due to hotel operation reasons (e.g. overbooking) or by customer request. Code is presented instead of designation for anonymity reasons
- `Babies`: Number of babies
- `BookingChanges`: Number of changes/amendments made to the booking from the moment the booking was entered on the PMS until the moment of check-in or cancellation (Calculated by adding the number of unique iterations that change some of the booking attributes, namely: persons, arrival date, nights, reserved room type or meal)
- `Children`: Number of children (Sum of both payable and non-payable children)
- `Company`: ID of the company/entity that made the booking or responsible for paying the booking. ID is presented instead of designation for anonymity reasons	(If 0.0 was given, it means that the booking is private)
- `Country`: Country of origin. Categories are represented in the ISO 3155–3:2013 format
- `CustomerType`: Type of booking, assuming one of four categories:	
    - Contract - when the booking has an allotment or other type of contract associated to it; 
    - Group – when the booking is associated to a group; 
    - Transient – when the booking is not part of a group or contract, and is not associated to other transient booking; 
    - Transient-party – when the booking is transient, but is associated to at least other transient booking
- `DaysInWaitingList`: Number of days the booking was in the waiting list before it was confirmed to the customer (Calculated by subtracting the date the booking was confirmed to the customer from the date the booking entered on the PMS)
- `DepositType`: Indication on if the customer made a deposit to guarantee the booking. This variable can assume three categories: (Calculated based on the payments identified for the booking in the transaction (TR) table before the booking׳s arrival or cancellation date.) 
    - No Deposit – no deposit was made; (In case no payments were found the value is “No Deposit”.) 
    - Non Refund – a deposit was made in the value of the total stay cost; (If the payment was equal or exceeded the total cost of stay, the value is set as “Non Refund”.)
    - Refundable – a deposit was made with a value under the total cost of stay. (Otherwise the value is set as “Refundable”)
- `DistributionChannel`: Booking distribution channel. The term “TA” means “Travel Agents” and “TO” means “Tour Operators”
- `IsCanceled`: Value indicating if the booking was canceled (1) or not (0)
- `IsRepeatedGuest`: Value indicating if the booking name was from a repeated guest (1) or not (0) (Variable created by verifying if a profile was associated with the booking customer. If so, and if the customer profile creation date was prior to the creation date for the booking on the PMS database it was assumed the booking was from a repeated guest)
- `LeadTime`: Number of days that elapsed between the entering date of the booking into the PMS and the arrival date (Subtraction of the entering date from the arrival date)
- `MarketSegment`: Market segment designation. In categories, the term “TA” means “Travel Agents” and “TO” means “Tour Operators”
- `Meal`: Type of meal booked. Categories are presented in standard hospitality meal packages:
    - Undefined/SC – no meal package;
    - BB – Bed & Breakfast;
    - HB – Half board (breakfast and one other meal – usually dinner);
    - FB – Full board (breakfast, lunch and dinner)
- `PreviousBookingsNotCanceled`: Number of previous bookings not cancelled by the customer prior to the current booking	(In case there was no customer profile associated with the booking, the value is set to 0. Otherwise, the value is the number of bookings with the same customer profile created before the current booking and not canceled.)
- `PreviousCancellations`: Number of previous bookings that were cancelled by the customer prior to the current booking	(In case there was no customer profile associated with the booking, the value is set to 0. Otherwise, the value is the number of bookings with the same customer profile created before the current booking and canceled.)
- `RequiredCardParkingSpaces`: Number of car parking spaces required by the customer
- `ReservationStatus`: Reservation last status, assuming one of three categories:
    - Canceled – booking was canceled by the customer;
    - Check-Out – customer has checked in but already departed;
    - No-Show – customer did not check-in and did inform the hotel of the reason why
- `ReservationStatusDate`: Date at which the last status was set. This variable can be used in conjunction with the ReservationStatus to understand when was the booking canceled or when did the customer checked-out of the hotel
- `ReservedRoomType`: Code of room type reserved. Code is presented instead of designation for anonymity reasons
- `StaysInWeekendNights`: Number of weekend nights (Saturday or Sunday) the guest stayed or booked to stay at the hotel	(Calculated by counting the number of weekend nights from the total number of nights)
- `StaysInWeekNights`: Number of week nights (Monday to Friday) the guest stayed or booked to stay at the hotel	(Calculated by counting the number of week nights from the total number of nights)
- `TotalOfSpecialRequests`: Number of special requests made by the customer (e.g. twin bed or high floor)

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
