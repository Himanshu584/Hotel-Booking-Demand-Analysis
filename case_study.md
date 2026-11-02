# Hotel Booking Demand Analysis — Case Study

## 1. Project Overview

This project analyzes hotel booking data to understand reservation patterns, cancellation behavior, pricing trends, seasonal demand, and customer preferences.

The analysis is conducted for a fictional hotel management scenario involving **Elite Hotels International**, with the goal of identifying actionable opportunities to improve reservation management, revenue planning, and operational efficiency.

The project uses Python to answer **25 business questions** across three levels of analysis:

- Basic Exploratory Data Analysis (10 questions)
- Intermediate Exploratory Data Analysis (10 questions)
- Advanced Analysis and Predictive Modeling (5 questions)

## 2. Business Problem

Hotel businesses face several operational and financial challenges, including booking cancellations, fluctuating demand, pricing uncertainty, and differences in customer booking behavior.

High cancellation rates can make occupancy and revenue forecasting difficult, while seasonal changes in demand complicate staffing and inventory planning.

Elite Hotels International wants to better understand these challenges using historical booking data.

The central business question is:

**How can hotel booking data be used to identify reservation patterns, investigate cancellation risk, understand pricing behavior, and support more informed business decisions?**

## 3. Project Objectives

1. Examine booking volumes, lead times, stay durations, and customer characteristics.
2. Measure cancellation rates and identify associated booking characteristics.
3. Analyze Average Daily Rate (ADR) across hotel types, market segments, and arrival periods.
4. Investigate seasonal booking patterns and estimate room revenue.
5. Compare customer behavior across booking channels and market segments.
6. Apply statistical and machine-learning techniques to investigate cancellation risk and ADR variation.
7. Translate analytical findings into practical business recommendations.

## 4. Dataset Information

**Dataset:** Hotel Booking Demand

**Source:** [Kaggle — Hotel Booking Demand](https://www.kaggle.com/datasets/jessemostipak/hotel-booking-demand)

**Original records:** 119,390

**Original columns:** 32

**Records after cleaning:** 119,210

**Columns after feature engineering:** 35

The dataset contains booking information for City Hotels and Resort Hotels, including arrival dates, booking lead times, cancellation status, guest composition, room types, market segments, and pricing information.

### 4.1 Data Dictionary

| Variable | Description |
|---|---|
| `hotel` | Hotel category: City Hotel or Resort Hotel |
| `is_canceled` | Whether a booking was canceled (1) or not (0) |
| `lead_time` | Days between booking creation and scheduled arrival |
| `arrival_date_year` | Scheduled arrival year |
| `arrival_date_month` | Scheduled arrival month |
| `arrival_date_week_number` | Week number of scheduled arrival |
| `arrival_date_day_of_month` | Day of scheduled arrival |
| `stays_in_weekend_nights` | Number of weekend nights |
| `stays_in_week_nights` | Number of weekday nights |
| `adults` | Number of adults |
| `children` | Number of children |
| `babies` | Number of babies |
| `meal` | Meal package associated with the booking |
| `country` | Guest country code |
| `market_segment` | Booking market segment |
| `distribution_channel` | Channel through which the booking was distributed |
| `is_repeated_guest` | Indicator of a returning guest |
| `previous_cancellations` | Number of previous canceled bookings |
| `previous_bookings_not_canceled` | Number of previous non-canceled bookings |
| `reserved_room_type` | Reserved room category code |
| `assigned_room_type` | Assigned room category code |
| `booking_changes` | Number of recorded booking modifications |
| `deposit_type` | Deposit policy category |
| `agent` | Travel agency identifier |
| `company` | Company identifier |
| `days_in_waiting_list` | Number of days on the waiting list |
| `customer_type` | Customer classification |
| `adr` | Average Daily Rate |
| `required_car_parking_spaces` | Number of requested parking spaces |
| `total_of_special_requests` | Number of special requests |
| `reservation_status` | Final recorded reservation status |
| `reservation_status_date` | Date associated with the reservation status |

### 4.2 Engineered Features

| Feature | Description |
|---|---|
| `arrival_date` | Complete arrival date constructed from arrival components |
| `total_night_stays` | Weekend nights + weekday nights |
| `total_guests` | Adults + children + babies |

Additional temporary analytical features were created where required, such as lead-time categories and estimated room revenue.

## 5. Data Preparation

The following preprocessing decisions were applied:

- Filled missing `children` values with zero.
- Replaced missing `country` values with `"Unknown"`.
- Replaced missing `agent` and `company` identifiers with zero, representing unknown identifiers.
- Removed 180 records containing no guests.
- Retained fully duplicated records because unique booking identifiers were unavailable.
- Converted reservation status dates into datetime format.
- Constructed arrival dates and engineered stay-duration and guest-count features.
- Created a separate pricing dataset by excluding two extreme ADR observations.
- Retained zero-night bookings in the main dataset but excluded them where positive stay duration was necessary.

These decisions were made to preserve analytical consistency while acknowledging limitations in the underlying data.

## 6. Business Questions

### 6.1 Basic EDA

1. What is the average booking lead time?
2. What is the distribution of bookings across hotel types?
3. How many bookings were canceled, and what is the cancellation rate?
4. Which arrival months have the highest booking volumes?
5. What is the average number of special requests per booking?
6. Which countries contribute the most bookings?
7. What is the average ADR for each hotel type?
8. What percentage of bookings require parking spaces?
9. What are the average weekday, weekend, and total stay durations?
10. How many bookings have recorded travel agent identifiers?

### 6.2 Intermediate EDA

11. How do cancellation rates differ between City Hotels and Resort Hotels?
12. How does ADR vary across market segments?
13. What is the relationship between booking lead time and cancellation likelihood?
14. Which distribution channels generate the most bookings?
15. How