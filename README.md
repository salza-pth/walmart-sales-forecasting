# Walmart Sales Forecasting

This project analyzes Walmart sales data using Apache PySpark to understand weekly sales patterns and build a sales forecasting model.

The project was completed using PySpark in Google Colab. The results were also visualized using Power BI to compare sales performance across stores, departments, time periods, and other business factors.

## Project Overview

The analysis and modeling focus on:

* Processing large-scale retail sales data using PySpark.
* Combining sales data with store information and external features.
* Handling missing values and preparing the dataset.
* Creating time-based and categorical features.
* Building regression models to predict weekly sales.
* Evaluating model performance using R² and RMSE.
* Visualizing sales patterns through Power BI.

## Dataset

The dataset comes from the Walmart Sales Forecasting competition on Kaggle.

The project uses four main datasets:

* `train - Walmart Sales Forecasting.csv` - Historical weekly sales data.
* `test - Walmart Sales Forecasting.csv` - Data without sales labels.
* `stores - Walmart Sales Forecasting.csv` - Store information, including store type and size.
* `features - Walmart Sales Forecasting.csv` - Additional information such as temperature, fuel price, CPI, unemployment, and promotional markdowns.

The training dataset contains 421,570 records from 45 stores and 81 departments between 2010 and 2012.

## Data Preparation

Several data preparation steps were performed before building the models:

* Joining the sales, store, and features datasets.
* Handling missing values in the macroeconomic and promotional columns.
* Filling missing markdown values with zero.
* Imputing missing CPI and unemployment values using median values.
* Extracting year, month, day, week, and day of week from the date column.
* Converting categorical variables into numerical features.
* Applying `StringIndexer` and `OneHotEncoder` to the Store and Dept columns.
* Combining the features using `VectorAssembler`.

A time-based split was also applied using June 1, 2012 as the cutoff date. This resulted in 356,489 training records and 65,081 testing records.

## Modeling

Two regression models were trained using PySpark MLlib:

* Linear Regression
* Random Forest Regressor

The models were evaluated after aggregating the predictions at the store level.

### Model Results

| Model                   | R² Score |   RMSE |
| ----------------------- | -------: | -----: |
| Linear Regression       |   94.22% | 12.33% |
| Random Forest Regressor |   81.70% | 21.94% |

Linear Regression produced the better result after the predictions were aggregated at the store level. The model was able to capture the general relationship between store characteristics, macroeconomic factors, and total weekly sales.

## Main Findings

Some of the main findings include:

* Type A stores generate the highest revenue compared to Type B and Type C stores.
* Store 20 recorded the highest cumulative sales among the stores analyzed.
* Total annual sales reached around $2.5 billion in 2011.
* July was the highest revenue month based on the analysis.
* Non-holiday weeks contributed more revenue than holiday weeks.
* Sales performance was generally higher when the temperature was between 70°F and 75°F.
* Linear Regression performed better than Random Forest after the predictions were aggregated at the store level.

## Tools Used

* Python
* Apache PySpark
* PySpark MLlib
* Spark SQL
* Google Colab
* Power BI
* Matplotlib
* Seaborn

## Project Files

* `Walmart_Sales_Forecasting_Model.ipynb` - Main PySpark analysis and modeling notebook.
* `train - Walmart Sales Forecasting.csv` - Historical sales dataset.
* `test - Walmart Sales Forecasting.csv` - Testing dataset.
* `stores - Walmart Sales Forecasting.csv` - Store information.
* `features - Walmart Sales Forecasting.csv` - Additional store and economic features.
* `walmart_processed.csv` - Processed dataset used for visualization.

## Project Limitations

The project was conducted using Google Colab, so the available computing resources limited the complexity of some models, especially Random Forest.

The dataset also contains missing promotional records, particularly in the earlier years. Other factors such as local weather conditions, competitors, and regional customer behavior are not included.

## Conclusion

This project shows how PySpark can be used to process and analyze large-scale retail data. The combination of distributed data processing, regression modeling, and Power BI visualization helps provide a better understanding of Walmart's sales performance and the factors related to weekly sales.
