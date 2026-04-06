<img width="900" height="639" alt="png-clipart-melbourne-skyline-city-building-illustration" src="https://github.com/user-attachments/assets/ea9ded3c-83d3-40a1-8110-2964b2a66d38" />


Melbourne Housing Market: Price Drivers & Predictive Analysis

Project Overview

The goal of this project is to identify key factors influencing housing prices in Melbourne and prepare data for building predictive models. Melbourne's property market is highly volatile, and understanding key features helps investors and buyers make informed decisions.

Tech Stack

Language: Python 3

Libraries: Pandas, NumPy (data processing), Matplotlib, Seaborn (visualization).

Key Project Stages

1. Data Cleaning & Preprocessing

The dataset contained a significant number of missing values and outliers. The following steps were performed:

Missing Values: Filling missing values in numerical features (BuildingArea, YearBuilt) with the median, and in categorical features with the mode.

Outlier Removal: Removing abnormally high prices (above the 99th percentile) to improve the stability of future models.

Data Formatting: Converting dates to datetime format to extract temporal features.

2. Feature Engineering

To improve the quality of the analysis, new derived features were created:

HouseAge: Building age as of 2025.

RoomDensity: Ratio of number of rooms to plot area.

Time Features: Extracting the year (SaleYear) and month (SaleMonth) of sale.

3. Exploratory Data Analysis (EDA)

The analysis visualized:

Correlation between price and physical characteristics (Building Area, Rooms).
<img width="1008" height="920" alt="HH" src="https://github.com/user-attachments/assets/3aead91a-9ea3-49d4-9bb1-7d2214bdccf4" />
Price distribution by region (Regionname) and property type.
<img width="691" height="470" alt="image" src="https://github.com/user-attachments/assets/25c6418e-0c02-41c5-aec4-536d322973a4" />

The influence of geographic location (Lattitude, Longitude) on price.

Results & Insights

Location Matters: Region of residence and proximity to the city center are the strongest price predictors.

<img width="1001" height="723" alt="image" src="https://github.com/user-attachments/assets/dd006ed5-9dfe-4d75-abc5-5bd86f855720" />

Size vs. Price: A strong positive correlation was found between the living area (BuildingArea) and the final price.

<img width="691" height="470" alt="pp" src="https://github.com/user-attachments/assets/6bab2257-58dc-4e8f-8923-1ccd209448b6" />

Age Factor: New construction and historic buildings are valued higher than middle-aged homes (U-shaped relationship).

<img width="691" height="470" alt="image" src="https://github.com/user-attachments/assets/f065527a-db42-4a61-898e-b83a28e8beab" />

Investing in spacious properties in prime locations (closer to the center and south) remains the safest and most profitable strategy, according to historical data from over 13,500 records.

Repository Structure

melbourne_housing.ipynb — the main Jupyter Notebook containing the cleaning and analysis process.

melb_data.csv — the original dataset.

Melbourne_cleaned.csv - Cleaned data ready for Machine Learning.
