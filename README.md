# E-Commerce vs Traditional Retail: Data-Driven Analysis and Impact Assessment

## Report: E-commerce and its Impact on Traditional Retail  

### Data Collection 
For this project, I was tasked with finding datasets that included the following columns: 
- E-commerce sales volumes and growth rates 
- Traditional retail sales figures 
- Consumer behavior metrics (e.g., online vs. in-store preferences) 
- Market share of major e-commerce platforms 
- Economic indicators affecting retail (e.g., disposable income, unemployment rates) 

Initially, I spent significant time searching for a single dataset containing all of these columns. However, after consulting with my instructor, I was advised to collect multiple datasets, each containing a different relevant column. Following this guidance, I gathered three datasets: 

- **Dataset 1**: [Women Clothing E-commerce Sales](https://www.kaggle.com/datasets/shilongzhuang/-women-clothing-ecommerce-sales-data)
  - Contains information on e-commerce sales volumes and growth rates. 
- **Dataset 2**: [Consumer Behavior and Shopping Habits](https://www.kaggle.com/datasets/zeesolver/consumer-behavior-and-shopping-habits-dataset)
  - Provides insights into consumer behavior, specifically their preferences for online vs. in-store shopping. 
- **Dataset 3**: [Economic Indicators - Unemployment Rates](https://data.worldbank.org/indicator/SL.UEM.TOTL.ZS?locations=4E)
  - Relevant data on economic indicators such as unemployment rates.

### Data Loading 
The three datasets were loaded into separate pandas DataFrames using `pd.read_excel()` and `openpyxl` engine. I focused on the first sheet of Dataset 3 by specifying the `sheet_name='Data'` argument.

### Data Inspection 
To inspect the structure of the DataFrames, I used the `head()` function to get an initial look at each dataset.

### Data Preprocessing 
- **Dataset 3 Preprocessing**: The first three rows were irrelevant and were skipped using the `skiprows` parameter.
- **Year Selection**: Data from Dataset 3 was filtered for 2022 to match the time frame of the other two datasets.

### Data Merging 
The datasets were merged using the `pd.merge()` function based on common columns like size and color in Datasets 1 and 2. Dataset 3, which used country codes, required adding a country code column to the merged DataFrame.

### Data Preprocessing and Cleaning 

#### Missing Value Analysis 
1. **Dropping Columns Based on Missing Data Threshold**: Columns with more than 50% missing values were dropped.
2. **Imputing Missing Values in Numerical Columns**: Missing values were filled using the median.
3. **Imputing Missing Values in Categorical Columns**: Categorical columns were imputed using the mode, followed by `infer_objects()` to ensure proper data types.

#### Outlier Detection and Handling 
1. **IQR Method**: Used to detect and handle outliers.
2. **Z-score Method**: Outliers beyond 3 standard deviations from the mean were removed.

### Feature Scaling and Normalization 
1. **Constant Column Detection**: Constant columns were removed.
2. **Normalization**: Numerical columns were normalized using Min-Max scaling.

### Categorical Data Handling 
- **Label Encoding**: Categorical columns were label-encoded for compatibility with machine learning algorithms.

### Feature Engineering 
1. **Discount Impact**: Percentage discount on the unit price compared to the purchase amount.
2. **Purchase Frequency Index**: Frequency of purchases multiplied by previous purchases to assess customer loyalty.

### Principal Component Analysis (PCA) 
1. **Standardizing Data**: The data was standardized before applying PCA.
2. **Explained Variance**: PCA components were selected to retain 95% of the variance.
3. **Visualizing Principal Components**: Visualized the first two principal components to identify relationships.

### Customer Analysis and CLV Modeling 
1. **Calculating Average Purchase Value (APV)**: Total revenue divided by quantity purchased.
2. **Purchase Frequency and Customer Lifespan**: Calculated based on unique months of purchases.
3. **Customer Lifetime Value (CLV)**: Used APV, Purchase Frequency, and Customer Lifespan to estimate CLV.
4. **CLV-Based Customer Segmentation**: Segmented and visualized CLV distribution across customer segments.

### Scenario Analysis 
1. **Impact of Changes in Average Purchase Value on CLV**:
    - **APV Increase**: A 10% increase in APV modeled higher CLV.
    - **APV Decrease**: A 10% decrease showed a reduction in CLV.

### Visual Insights 
1. **Purchase Frequency and Customer Lifespan Distribution**: Histograms and density plots visualized purchase behavior.
2. **Variance Explained by PCA**: Visualized to determine the optimal number of components.
3. **CLV Distribution Across Customer Segments**: Identified key differences across segments using boxplots and histograms.

### Insights and Narrative 

#### a) Five Key Insights about Global E-commerce Trends and their Impact on Traditional Retail: 
1. **CLV Disparity Across Segments**: High-value customer segments drive significant revenue in e-commerce.
2. **Customer Retention Boosts CLV**: E-commerce platforms excel at customer retention compared to traditional retail.
3. **Purchase Frequency and Profitability**: E-commerce customers shop more frequently than traditional retail customers.
4. **Sensitivity of CLV to APV**: Small changes in APV significantly affect CLV.
5. **Customer Demographics and Seasonal Trends**: E-commerce platforms better adapt to seasonal trends.

#### b) Narrative of Retail Industry Transformation: 
E-commerce has fundamentally transformed retail by leveraging customer data to optimize acquisition and retention, providing a competitive edge over traditional retail.

#### c) Actionable Recommendations: 

**For Traditional Retailers**:
- Adopt omnichannel strategies.
- Leverage in-store technology.
- Use data for personalized experiences.

**For E-commerce Platforms**:
- Enhance customer retention programs.
- Optimize supply chain and logistics.
- Diversify product offerings.

**For Policymakers**:
- Support small retailers in digital transition.
- Regulate data privacy.
- Encourage fair competition.

### Conclusion 
The retail industry is transforming due to e-commerce dominance. Traditional retailers must adapt by integrating digital tools, while e-commerce platforms should continue innovating to sustain growth.
