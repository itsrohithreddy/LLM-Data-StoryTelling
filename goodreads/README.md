# Analysis Report for `.\goodreads`

## Dataset Overview

- **Number of Rows**: 10,000
- **Number of Columns**: 23
- **Columns**:
  - `book_id`
  - `goodreads_book_id`
  - `best_book_id`
  - `work_id`
  - `books_count`
  - `isbn`
  - `isbn13`
  - `authors`
  - `original_publication_year`
  - `original_title`
  - `title`
  - `language_code`
  - `average_rating`
  - `ratings_count`
  - `work_ratings_count`
  - `work_text_reviews_count`
  - `ratings_1`
  - `ratings_2`
  - `ratings_3`
  - `ratings_4`
  - `ratings_5`
  - `image_url`
  - `small_image_url`

## Sample Data

| book_id | goodreads_book_id | best_book_id | work_id | books_count | isbn         | isbn13                 | authors                        | original_publication_year | original_title                                 | title                                           | language_code | average_rating | ratings_count | work_ratings_count | work_text_reviews_count | ratings_1 | ratings_2 | ratings_3 | ratings_4 | ratings_5 | image_url                                                    | small_image_url                                                |
|---------|--------------------|---------------|---------|-------------|--------------|-------------------------|--------------------------------|--------------------------|--------------------------------------------------|--------------------------------------------------|---------------|----------------|-----------------|-----------------------|--------------------------|-----------|-----------|-----------|-----------|-----------|--------------------------------------------------------------|--------------------------------------------------------------|
| 1       | 2767052            | 2767052       | 2792775 | 272         | 439023483    | 9.78043902348e+12       | Suzanne Collins               | 2008.0                   | The Hunger Games                              | The Hunger Games (The Hunger Games, #1)     | eng           | 4.34           | 4780653        | 4942365              | 155254                 | 66715     | 127936    | 560092    | 1481305   | 2706317   | ![image](https://images.gr-assets.com/books/1447303603m/2767052.jpg) | ![image](https://images.gr-assets.com/books/1447303603s/2767052.jpg) |
| 2       | 3                  | 3             | 4640799 | 491         | 439554934    | 9.78043955493e+12       | J.K. Rowling, Mary GrandPré   | 1997.0                   | Harry Potter and the Philosopher's Stone       | Harry Potter and the Sorcerer's Stone (Harry Potter, #1) | eng           | 4.44           | 4602479        | 4800065              | 75867                  | 75504     | 101676    | 455024    | 1156318   | 3011543   | ![image](https://images.gr-assets.com/books/1474154022m/3.jpg) | ![image](https://images.gr-assets.com/books/1474154022s/3.jpg) |

## Key Insights from Analysis

### Basic Analysis

- **Missing Values**:
  - No missing values across all columns.

### Preprocessing Insights

- **Imputation Strategies**:
  - `isbn`: Replaced with 'Unknown' since it’s a unique identifier.
  - `isbn13`: Mean used as it’s numeric.
  - `original_publication_year`: Median to account for skew.
  - `original_title`: Filled with 'Unknown'.
  - `language_code`: Most frequent filled.

### Binnable Columns Insights

- **Binnable Columns**:
  - `books_count`, `original_publication_year`, `average_rating`, `ratings_count`, `work_ratings_count`, `work_text_reviews_count`, `ratings_1`, `ratings_2`, `ratings_3`, `ratings_4`, `ratings_5` are suitable for binning.
  - Unique identifier columns are not suitable for binning.

### Skewness Category

- **Features on Skewness**:
  - **Right-Skewed**: `books_count`, `ratings_count`, `work_ratings_count`, `work_text_reviews_count`, `ratings_1`, `ratings_2`, `ratings_3`, `ratings_4`, `ratings_5`.
  - **Normally Distributed**: `average_rating`.

## Visualizations and Insights

### Binnable Columns Distribution
![binnable_columns_distribution.png](./goodreads/binnable_columns_distribution.png)
- **Observations**:
  1. **Book Count**: Right-skewed - most books have fewer counts.
  2. **Average Rating**: Normal distribution around 0.5.
  3. **Ratings Count**: Right skew - few books receive many ratings.
  4. **Reviews Count**: Many books have few reviews.

### Correlation Matrix
![correlation_matrix.png](./goodreads/correlation_matrix.png)
- **Observations**:
  1. **Strongest Positive**: Between `ratings_1` and `average_rating` (0.94).
  2. **Negative Correlations**: `ratings_4` (0.67) and `ratings_5` (-0.73).
  3. **Moderate Correlation**: `publication_year` and `average_rating` (-0.42).
  4. **Redundant Data**: Strong correlations among `book_id`, `goodreads_book_id`, `best_book_id`, and `work_id`.

### KMeans Clustering
![kmeans_clustering.png](./goodreads/kmeans_clustering.png)
- **Observations**:
  1. Significant separation between clusters.
  2. Possible outliers in Cluster 0.
  3. Non-linear patterns suggested.
  4. Clusters 1 and 2 are denser.

### Ratings Count vs Work Ratings Count
![scatter_plot.png](./goodreads/scatter_plot.png)
- **Observations**:
  1. Strong positive correlation.
  2. Linear relationship indicated.
  3. Consistent data spread.
  4. Potential for predictive modeling.

## Recommendations and Next Steps

- **Data Quality Improvements**: Address missing values and outliers.
- **Future Exploration**: Utilize clustering and PCA for segmentation and analysis.
- **Operational Use Cases**: Leverage time-series and geospatial trends for strategic decision-making.

## License
This project is licensed under the MIT License.