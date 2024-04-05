# Store Sales Time Series Forecasting

This repository contains the code and analysis for a time series forecasting project aimed at predicting the sales of various product families at Favorita, a large retail supermarket chain in Ecuador. The project is based on a Kaggle competition and utilizes several datasets including sales data, store information, oil prices, and holidays events to model and predict daily sales across multiple stores.

## Overview

The goal of this project is to forecast daily sales for 33 product families across multiple Favorita stores located in Ecuador. Given Ecuador's economy's sensitivity to oil prices, this project also considers external factors such as oil price trends and holiday events in its analysis and modeling. 

## Datasets

The project utilizes the following datasets:

- `train.csv` and `test.csv`: Contain the main sales data for training and testing the models, respectively. Each record provides information on the date, store number, product family, sales, and the number of items on promotion.
- `stores.csv`: Includes metadata about the stores, such as the city, state, type, and cluster.
- `oil.csv`: Daily oil prices, an important economic factor for Ecuador.
- `holidays_events.csv`: Lists holidays and events, providing context on potential sales spikes or drops.

## Exploratory Data Analysis (EDA)

The EDA process involved analyzing sales trends over time, understanding the distribution of sales across stores and product families, and examining the impact of promotions and external factors like oil prices and holiday events on sales. Key steps included:

- Inspecting data for null values and data types.
- Generating descriptive statistics for sales, store counts, and product families.
- Temporal analysis of sales trends, including the impact of paydays and the 2016 Ecuador earthquake.
- Analysis of promotions and their impact on sales.
- Exploration of oil price trends.

## Visualizations

Throughout the Exploratory Data Analysis (EDA) phase, various visualizations were created to understand the data better and gain insights into the sales trends. Below are descriptions of some key visualizations:

**Total Daily Sales Across All Stores**

A line plot showcasing the total daily sales across all stores, highlighting the general sales trend and identifying any significant spikes or drops, which could correspond to holidays, promotions, or external events like the 2016 Ecuador earthquake.

**Sales by Product Family**

A bar plot representing the total sales for each product family, allowing us to identify which product families contribute most to the overall sales. This visualization helps in understanding the product mix and prioritizing stock levels and promotions.

**Impact of Promotions on Sales**

A line plot that compares the total promotional items with the overall sales trends. This visualization elucidates the effectiveness of promotions in driving sales across different periods.

**Oil Price Trends**

Given the economic sensitivity of Ecuador to oil prices, a line plot of daily oil prices was created to investigate any correlation between oil price fluctuations and supermarket sales.

**Sales Distribution by Stores and Cities**

- A treemap to visualize the distribution of sales among different stores and cities, highlighting the contribution of each store to the total sales volume. This visualization aids in identifying key geographical areas for business growth or optimization.

**Temporal Sales Trends**

Several plots were crafted to dissect sales trends over different timeframes, including:
- Daily and Average Sales: A comparison of daily sales with their rolling average, delineating underlying trends and smoothing out day-to-day volatility.
- Monthly and Quarterly Sales: Bar plots to illustrate sales variations across months and quarters, identifying seasonal trends and the impact of specific months or quarters on the overall sales performance.

**Promotional Item Trends**

A visualization showcasing the trend of promotional items over time, aligned with sales data to assess how promotions influence sales dynamics and customer purchasing behavior.

These visualizations form the backbone of our EDA, offering profound insights into sales trends, the impact of external factors, and operational strategies that could optimize sales performance. They are instrumental in guiding the subsequent modeling phase, ensuring that our predictive models are well-informed by the underlying data patterns and insights.



## Feature Engineering

The project extensively uses feature engineering to enhance model performance, including:

- Creating time-related features such as day of the week, month, quarter, and year.
- Incorporating external data such as oil prices and holiday events.
- Labeling days as working days, weekends, and identifying salary days.

## Modeling

A machine learning pipeline was developed for forecasting, using scikit-learn and XGBoost. The approach involved:

- Preprocessing data with pipelines for numerical and categorical features.
- Training individual models for each product family to capture unique sales patterns.
- Utilizing an enhanced time series cross-validation method to evaluate models without data leakage.
- Hyperparameter tuning to optimize model performance.

**Individual Models for Each Product Family**

The decision to build individual models for each product family was driven by several factors intrinsic to the nature of retail sales forecasting:

- **Product Distinctiveness**: Each product family typically exhibits unique sales patterns and trends influenced by factors such as seasonal demand, promotions, and consumer preferences. A single model might not capture these nuances effectively.

- **Feature Interaction**: Different families may have varying relationships with the predictors. For example, the effect of a national holiday on food items might be different from that on clothing. Separate models allow for these distinct interactions to be learned more effectively.

- **Model Complexity**: Combining all families into a single model could lead to a complex model that is hard to optimize and may require extensive computational resources. Individual models simplify the training process and can be more interpretable.

- **Target Scale Variability**: Sales volumes can vary significantly across families. If a single model is used, it may become biased towards families with higher sales volumes, potentially at the expense of accuracy in predicting sales for families with lower volumes.

- **Promotion Sensitivity**: The impact of promotions may vary widely across different product families. Individual models allow for a more tailored approach to understanding how promotions affect each family's sales.

- **Inventory Management**: For supply chain and inventory management, having specific predictions for each family helps in precise stock planning, reducing the risk of overstocking or stockouts.

- **Model Adaptability**: Separate models allow for flexibility in updating and maintaining the forecasting system. If sales dynamics change for a particular family, only the relevant model needs to be retrained, without affecting the others.

- **Performance Optimization**: By building individual models, we could fine-tune and optimize each model's hyperparameters specifically for the sales behavior of each family, leading to more accurate predictions.

In summary, creating individual models for each product family allowed us to tailor the forecasting to the specific characteristics and sales dynamics of each category, thereby enhancing the accuracy and usefulness of our predictive insights.


## Predictions and Submission

The project concludes with generating sales forecasts for the test dataset, handling zero sales for certain product families based on recent sales data, and preparing a submission file for the Kaggle competition.


## Conclusion

This project highlights the complexity of forecasting sales in a retail environment, demonstrating the importance of understanding external factors and employing detailed feature engineering to improve prediction accuracy. It showcases a methodical approach to time series prediction, capable of handling real-world data challenges.

