# Exploratory Data Analysis (EDA) on Coffee Quality

## Introduction
This project focuses on performing an exploratory data analysis (EDA) on coffee quality data. The goal is to clean, preprocess, and analyze the dataset to derive meaningful insights.

## Data Preprocessing Steps

### Handling Missing Values
- Dropped columns with less than 5% missing values.
- Dropped `lot_number` as 79% of values were missing.

### Processing Date Variables
- Converted `harvest_year`, `grading_date`, and `expiration` to datetime format.
- Found that `expiration` is consistently 365 days from `grading_date`, so dropped `expiration`.

### Handling Categorical Variables
- Considered `species`, `country_of_origin`, `region`, `variety`, `processing_method`, and `color` as categorical variables since they provide direct information about coffee beans.
- Identified similarities in columns:
  - `owner` and `owner_1` are identical → Dropped `owner`
  - `certification_body` and `in_country_partner` are highly similar → Dropped `in_country_partner`
  - `farm_name` and `producer`, `company` and `in_country_partner` are similar but have distinctions → Kept both
  - `certification_address` and `certification_contact` retained for potential company location analysis

### Unit Conversion
- Converted weight from pounds (lbs) to kilograms (kg), using the conversion: **1 lb = 0.453 kg**

### Outlier Detection and Handling
- Boxplot analysis identified outliers in every numerical column.
- Checked for unrealistic values:
  - `altitude` > 4500m is considered unusual (above mountain regions)
  - `moisture` cannot be zero
  - `zero_number_of_bags` is unusual

## Insights from Data Analysis
- **Species Distribution:** Highly imbalanced with Arabica dominating.
- **Country of Origin:** Many unique values; grouped countries with less than 1% occurrences into an "Others" category.
- **Region Distribution:** Created three new categories to prevent "Others" from becoming the dominant category.
- **Variety Distribution:** Similar cluttering issue, but an "Others" category already exists; introduced `minor_others` for varieties representing <1% of data.
- **Color:** The dataset had "None" values, which were categorized as "Others."

## Next Steps
- Conduct feature engineering to improve data quality for predictive modeling.
- Perform correlation analysis to determine key factors influencing coffee quality.
- Build predictive models using the cleaned dataset.

## Conclusion
This EDA provides a structured approach to understanding coffee quality data, identifying inconsistencies, and preparing the dataset for further analysis or modeling. Future work will focus on leveraging this cleaned data to build machine learning models for quality prediction.
