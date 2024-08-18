# WALMART-SALES-FORECAST

﻿# Walmart Sales Time Series Forecasting Using Machine 
 Time Series Forecasting of Walmart Sales Data using Machine Learning

# The motive of Walmart Time Series Forecast machine learning project , is typically to predict future values of a dataset based on historical data. For Walmart, this might involve predicting future sales, inventory levels, or demand for specific products. The primary goals could include:

## 	1. Optimizing Inventory Management: Predicting future sales helps Walmart ensure that they stock the right amount of products, reducing both overstock and stockouts.
## 	2. Improving Supply Chain Efficiency: By forecasting demand, Walmart can better manage its supply chain, ensuring timely deliveries and minimizing logistical costs.
## 	3. Enhancing Pricing Strategies: Accurate forecasts allow Walmart to adjust pricing strategies dynamically based on expected demand.
## 	4. Resource Allocation: Walmart can better allocate resources like staffing, marketing efforts, and shelf space based on expected trends.
##      5. Strategic Planning: Long-term forecasts assist in planning business strategies, such as opening new stores or expanding into new markets.

## Blog of this Project
## Datasets
**Walmart Recruiting - Store Sales Forecasting** downloaded from
https://www.kaggle.com/c/walmart-recruiting-store-sales-forecasting
 - **train.csv** - CSV Data file containing following attributes
	- Store
	- Dept
	- Date
	- Weekly_Sales
	- IsHoliday

115064 Data rows
 - **stores.csv** - CSV Data File containing following attributes 
	 - Store
	 - Type
	 - Size
	 
45 Data rows
 - **features.csv** - CSV Data file containing following attributes
	- Store
	- Date
	- Temperature
	- Fuel_Price
	- MarkDown1
	- MarkDown2
	- MarkDown3
	- MarkDown4
	- MarkDown5
	- CPI
	- Unemployment
	- IsHoliday
	
8190 Data rows
## Machine Learning Models
- Linear Regression Model
- Random Forest Regression Model
- K Neighbors Regression Model
- XGBoost Regression Model
## Data Preprocessing
- ### **Handling Missing Values**
	- CPI, Unemployment of features dataset had 585 null values.
	- MarkDown1 had 4158 null values
	- MarkDown2 had 5269 null values
	- MarkDown3 had 4577 null values
	- MarkDown4 had 4726 null values
	- MarkDown5 had 4140 null values
	All missing values were filled using median of respective columns.
- ### **Merging Datasets**
	- Main Dataset merged with stores dataset
	- Resulting Dataset merged with features dataset
	- Total data rows 421570 and 15 attributes
	- Date column converted into datetime data type
	- Date attribute set as index of combined dataset
- ### **Splitting Date Column**
	- Split the Date column into Year, Month, Week
- ### **Aggregate Weekly Sales**
	- Create max, min, mean, median, std of weekly sales 
- ### **Outlier Detection and Other abnormalities**
	- Markdowns were summed into Total_MarkDown
	- Outliers were removed using z-score
	- Data rows 375438 and 20 columns
	- Negative weekly sales were removed
	- 374247 Data rows and 20 columns
- ### **One-hot-encoding**
	- Store, Dept, Type columns were one-hot-encoded using get_dummies method
	- After one-hot-encoding, no. of columns becomes 145
- ### **Data Normalization**
	- Numerical columns normalized using MinMaxScaler in the range 0 to 1 
- ### **Recursive Feature Elimination**
	- Random Forest Regressor used to calculate feature ranks and importance with 23 estimators
	-  Features selected to retain
		- mean, median, Week, Temperature, max, CPI, Fuel_Price, min, std, Unemployment, Month, Total_MarkDown, Dept_16, Dept_18, IsHoliday, Dept_3, Size, Dept_9, Year, Dept_11, Dept_1, Dept_5, Dept_56
	- No. of attributes after feature elimination - 24
## Splitting Dataset
- Dataset was splitted into 80% for training and 20% for testing
- Target feature - Weekly_Sales 
## Linear Regression Model
- Linear Regressor Accuracy - 92.391573
- Mean Absolute Error - 0.029839
- Mean Squared Error - 0.003389
- Root Mean Squared Error - 0.058221
- R2 - 0.0.923917
- `LinearRegression(copy_X=True, fit_intercept=True, n_jobs=None)`
## Random Forest Regression Model
- Random Forest Regressor Accuracy - 97.891836
- Mean Absolute Error - 0.015471
- Mean Squared Error - 0.000939 
- Root Mean Squared Error - 0.030646 
- R2 - 0.978921
- n_estimators - 100
- `RandomForestRegressor(bootstrap=True, ccp_alpha=0.0, criterion='mse', max_depth=None, max_features='auto', max_leaf_nodes=None, max_samples=None, min_impurity_decrease=0.0, min_impurity_split=None, min_samples_leaf=1, min_samples_split=2, min_weight_fraction_leaf=0.0, n_estimators=100, n_jobs=None, oob_score=False, random_state=None, verbose=0, warm_start=False)`
## K Neighbors Regression Model
- KNeigbhbors Regressor Accuracy - 91.8176
- Mean Absolute Error - 0.033361
- Mean Squared Error - 0.0036454
- Root Mean Squared Error - 0.0603774
- R2 - 0.918368
- Neighbors - 1
- `KNeighborsRegressor(algorithm='auto', leaf_size=30, metric='minkowski', metric_params=None, n_jobs=None, n_neighbors=1, p=2, weights='uniform')`
## XGBoost Regression Model
- XGBoost Regressor Accuracy - 97.307579
- Mean Absolute Error - 0.0197942
- Mean Squared Error - 0.001199
- Root Mean Squared Error - 0.0346343
- R2 - 0.973076844
- Learning Rate - 0.1
- n_estimators - 100
- `XGBRegressor(base_score=0.5, booster='gbtree', colsample_bylevel=1, colsample_bynode=1, colsample_bytree=1, gamma=0, importance_type='gain', learning_rate=0.1, max_delta_step=0, max_depth=3, min_child_weight=1, missing=None, n_estimators=100, n_jobs=1, nthread=None, objective='reg:linear', random_state=0, reg_alpha=0, reg_lambda=1, scale_pos_weight=1, seed=None, silent=None, subsample=1, verbosity=1)`
## Comparing Models
- Linear Regressor Accuracy - 92.391573
- Random Forest Regressor Accuracy - 97.891836
- K Neighbors Regressor Accuracy - 91.8176
- XGBoost Accuracy - 97.307579
## Citations
- **Walmart Recruiting - Store Sales Forecasting**
https://www.kaggle.com/c/walmart-recruiting-store-sales-forecasting

