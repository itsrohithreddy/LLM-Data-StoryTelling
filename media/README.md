# Analysis Report for `./media`

## Dataset Overview
- **Number of Rows**: 2652  
- **Number of Columns**: 8  
- **Columns**:  
  - `date`  
  - `language`  
  - `type`  
  - `title`  
  - `by`  
  - `overall`  
  - `quality`  
  - `repeatability`  

## Sample Data
| Date       | Language | Type  | Title                      | By                        | Overall | Quality | Repeatability |
|------------|----------|-------|----------------------------|---------------------------|---------|---------|---------------|
| 15-Nov-24  | Tamil    | movie | Meiyazhagan                | Arvind Swamy, Karthi     | 4       | 5       | 1             |
| 10-Nov-24  | Tamil    | movie | Vettaiyan                 | Rajnikanth, Fahad Fazil   | 2       | 2       | 1             |
| 09-Nov-24  | Tamil    | movie | Amaran                     | Siva Karthikeyan, Sai Pallavi | 4       | 4       | 1             |
| 11-Oct-24  | Telugu   | movie | Kushi                      | Vijay Devarakonda, Samantha | 3       | 3       | 1             |
| 05-Oct-24  | Tamil    | movie | GOAT                       | Vijay                     | 3       | 3       | 1             |
| 02-Oct-24  | Telugu   | movie | Sanivaaram Saripodhaa     | Nani, SJ Surya            | 3       | 3       | 1             |
| 01-Oct-24  | Tamil    | movie | Saba Nayagan              | Ashok Selvan             | 3       | 3       | 2             |
| 30-Sep-24  | English   | movie | Dune: Part Two            | Timothée Chalamet, Zendaya | 3       | 4       | 1             |
| 10-Sep-24  | English   | movie | Spencer Confidential       | Mark Wahlberg            | 3       | 3       | 1             |

## Key Insights from Analysis
### Basic Analysis
- **Missing Values**:  
  {'date': 0, 'language': 0, 'type': 0, 'title': 0, 'by': 0, 'overall': 0, 'quality': 0, 'repeatability': 0}  

### Preprocessing Insights
- **Imputing Missing Values and Reasoning**:  
  - **Date**: Replace with 'mean' - Continuous values allow using the mean for null fill.  
  - **By**: Replace with 'most frequent' - Most representative value for categorical data.  

### Binnable Columns Insights
- **Binnable Columns and Reasoning**:  
  - **Overall**: Binnable - Numeric values can create discrete categories.  
  - **Quality**: Binnable - Numeric values can create discrete categories.  
  - **Repeatability**: Not Binnable - Limited numeric variation doesn't form meaningful bins.  

### Skewness Category
- **Features segregation on skewness**:  
  - **Left Skewed**: ['Quality Ratings']  
  - **Right Skewed**: ['Overall Ratings']  
  - **Normally Distributed**: []  

## Visualizations and Insights
### Overall Ratings and Quality Ratings Distribution
![binnable_columns_distribution.png](./media/binnable_columns_distribution.png)  
- **Chart Description**: Displays histograms of Overall Ratings and Quality Ratings with frequency counts and density plots.  
- **Insights**:  
  1. Bimodal distribution for both ratings, indicating a preference around scores of 3.0 and 4.0.  
  2. Users tend to score in mid-range more than extremes (1 and 5).  
  3. Suggests potential for differentiation in user experience and quality perception.  

### Correlation Analysis
![correlation_matrix.png](./media/correlation_matrix.png)  
- **Chart Description**: Correlation matrix heatmap of overall, quality, and repeatability scores.  
- **Insights**:  
  1. Strong correlation (0.83) between 'overall' and 'quality'.  
  2. Moderate correlation (0.51) between 'overall' and 'repeatability'.  
  3. Weaker correlation (0.31) between 'quality' and 'repeatability'.  

### KMeans Clustering Visualization
![kmeans_clustering.png](./media/kmeans_clustering.png)  
- **Chart Description**: KMeans clustering visual of PCA-transformed data.  
- **Insights**:  
  1. Three distinct clusters identified, visual representation confirms separation.  
  2. Cluster characteristics vary, suggesting different user segments.  

### Quality vs Overall Ratings Scatter Plot
![scatter_plot.png](./media/scatter_plot.png)  
- **Chart Description**: Scatter plot of quality versus overall ratings.  
- **Insights**:  
  - Perfect linear correlation exists between quality and overall scores, suggesting perceived quality influences overall rating.  

## Recommendations and Next Steps
- **Data Quality**: Address missing values and outliers for cleaner analysis.  
- **Future Exploration**: Utilize clustering and PCA for segmentation and dimensionality reduction.  
- **Operational Use**: Leverage time-series patterns for forecasting and geospatial trends for targeted decision-making.  

## License
This project is licensed under the MIT License.
