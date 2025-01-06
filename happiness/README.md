# Analysis Report for `./happiness`

## Dataset Overview

This analysis focuses on a dataset detailing happiness and well-being across various countries. Below is a summary of the dataset:

- **Number of Rows**: 2363  
- **Number of Columns**: 11  
- **Columns**:  
  - `Country name`  
  - `year`  
  - `Life Ladder`  
  - `Log GDP per capita`  
  - `Social support`  
  - `Healthy life expectancy at birth`  
  - `Freedom to make life choices`  
  - `Generosity`  
  - `Perceptions of corruption`  
  - `Positive affect`  
  - `Negative affect`

## Sample Data

Here is a glimpse of the data within the dataset:

| Country name | year | Life Ladder | Log GDP per capita | Social support | Healthy life expectancy at birth | Freedom to make life choices | Generosity | Perceptions of corruption | Positive affect | Negative affect |
|--------------|------|-------------|---------------------|----------------|-------------------------------|-----------------------------|------------|-------------------------|----------------|-----------------|
| Afghanistan  | 2008  | 3.724       | 7.350               | 0.451          | 50.500                        | 0.718                       | 0.164      | 0.882                  | 0.414          | 0.258           |
| Afghanistan  | 2009  | 4.402       | 7.509               | 0.552          | 50.800                        | 0.679                       | 0.187      | 0.850                  | 0.481          | 0.237           |
| Afghanistan  | 2010  | 4.758       | 7.614               | 0.539          | 51.100                        | 0.600                       | 0.118      | 0.707                  | 0.517          | 0.275           |
| Afghanistan  | 2011  | 3.832       | 7.581               | 0.521          | 51.400                        | 0.496                       | 0.160      | 0.731                  | 0.480          | 0.267           |
| Afghanistan  | 2012  | 3.783       | 7.661               | 0.521          | 51.700                        | 0.531                       | 0.234      | 0.776                  | 0.614          | 0.268           |

## Key Insights from Analysis

### Basic Analysis
- **Missing Values**:  
  - {'Country name': 0, 'year': 0, 'Life Ladder': 0, 'Log GDP per capita': 0, 'Social support': 0, 'Healthy life expectancy at birth': 0, 'Freedom to make life choices': 0, 'Generosity': 0, 'Perceptions of corruption': 0, 'Positive affect': 0, 'Negative affect': 0}

### Preprocessing Insights
- **Imputing Missing Values and Reasoning**:  
  - Columns such as `Log GDP per capita`, `Social support`, `Healthy life expectancy at birth`, `Freedom to make life choices`, `Generosity`, `Perceptions of corruption`, `Positive affect`, and `Negative affect` were imputed using their mean, as mean is suitable for continuous data expected to have a normal distribution.

### Binnable Columns Insights
- **Binnable Columns and Reasoning**:  
  - All columns except `Country name` can be binned to categorize data in a more meaningful way.
    - **Examples**: 
      - `year` - Discrete variable. 
      - `Life Ladder` - Continuous measurement.
      - `Log GDP per capita` - Segmented into GDP levels.

### Skewness Category
- **Features Segregation by Skewness**:  
  - **Left Skewed**: `Log GDP per capita`, `Healthy life expectancy at birth`  
  - **Right Skewed**: `year`, `Social support`, `Freedom to make life choices`, `Generosity`, `Perceptions of corruption`, `Positive affect`, `Negative affect`  
  - **Normally Distributed**: `Life Ladder`

## Visualizations and Insights

### 1. Binnable Columns Distribution
![binnable_columns_distribution.png](./happiness/binnable_columns_distribution.png)
- **Description**: This chart displays the distribution of various metrics related to quality of life and well-being across different countries. 

### 2. Correlation Matrix
![correlation_matrix.png](./happiness/correlation_matrix.png)
- **Description**: A heatmap showing relationships between social and economic factors. 
  - **Insights**:
    - Strong positive correlation between `life ladder` and `social support` (0.77).
    - Moderate positive correlation between `generosity` and `life ladder` (0.58).
    - Significant negative correlation between `generosity` and `corruption` (-0.46).

### 3. KMeans Clustering
![kmeans_clustering.png](./happiness/kmeans_clustering.png)
- **Description**: Results of KMeans clustering showing three distinct clusters.

### 4. Scatter Plot
![scatter_plot.png](./happiness/scatter_plot.png)
- **Description**: Relationship between `Log GDP per capita` and `Healthy life expectancy at birth` displays notable trends and insights regarding health outcomes relative to wealth.

## Recommendations and Next Steps
- **Data Quality**: Ensure missing value imputation and outlier handling.
- **Future Exploration**: Utilize clustering for segmentation insights.
- **Operational Use**: Leverage findings for decision-making and targeted interventions.

## License
This project is licensed under the MIT License.