# Data Analysis

This project involves analyzing the World Happiness Report data from 2015 to 2019 using Pandas and NumPy. The analysis includes retrieving specific subsets of data, identifying outliers, examining correlations, and visualizing trends.

## Features

1. **Data Loading**: Load datasets for the years 2015 to 2019 into Pandas DataFrames.
2. **Filtering and Retrieval**:
    - Retrieve countries in 2015 with Health (Life Expectancy) values between 0.5 and 1.
    - Retrieve the top 10 countries with the highest Happiness Score for the year 2016.
3. **Aggregation**: Calculate the mean Happiness Score grouped by region for any given year.
4. **Outlier Detection**: Identify outliers in the Happiness Score for each dataset from 2015 to 2019 using box plots.
5. **Correlation Analysis**: Analyze the relationship between the Happiness Score and Economy (GDP per Capita) using scatter plots.
6. **Data Integration**: Combine datasets from 2015 to 2019 into a single DataFrame with columns for Country, Region, Year, and Happiness Score for each year.
7. **Trend Analysis**: Visualize trends in Happiness Score over the years for selected countries.
8. **Regional Analysis**: Identify regions with an Economy (GDP per Capita) value less than 0.5 for the year 2015.
9. **Correlation Identification**: Identify the variables with the highest correlations across all countries for the years 2015 and 2016.

## Prerequisites

- Python 3.x
- Pandas
- NumPy
- Matplotlib (for visualizations)

## Usage

1. Clone the repository:
    ```sh
    git clone https://github.com/yourusername/world-happiness-report-analysis.git
    ```
2. Navigate to the project directory:
    ```sh
    cd world-happiness-report-analysis
    ```
3. Ensure the datasets are placed in the project directory with filenames `2015 - 2015.csv`, `2016 - 2016.csv`, `2017 - 2017.csv`, `2018 - 2018.csv`, and `2019 - 2019.csv`.
4. Run the script:
    ```sh
    python analysis_script.py
    ```

## Code Explanation

- **Data Loading**: Load datasets for the years 2015 to 2019:
    ```python
    import pandas as pd
    import numpy as np
    df1 = pd.read_csv('2015 - 2015.csv')
    df2 = pd.read_csv('2016 - 2016.csv')
    df3 = pd.read_csv('2017 - 2017.csv')
    df4 = pd.read_csv('2018 - 2018.csv')
    df5 = pd.read_csv('2019 - 2019.csv')
    ```

- **Filtering and Retrieval**: Examples of retrieving specific subsets of data:
    ```python
    df1[(df1['Health (Life Expectancy)'] >= 0.5) & (df1['Health (Life Expectancy)'] <= 1)]['Country']
    df2.sort_values(by='Happiness Score', ascending=False).head(10)['Country']
    ```

- **Aggregation**: Calculate mean Happiness Score grouped by region:
    ```python
    df1.groupby('Region')['Happiness Score'].mean()
    ```

- **Outlier Detection**: Identify outliers using box plots:
    ```python
    df1.boxplot(column='Happiness Score')
    # Similarly for df2, df3, df4, df5
    ```

- **Correlation Analysis**: Scatter plots to analyze relationships:
    ```python
    df1.plot.scatter(x='Happiness Score', y='Economy (GDP per Capita)')
    # Similarly for df2, df3, df4, df5
    ```

- **Data Integration**: Combine datasets into a single DataFrame:
    ```python
    df1['Year'] = 2015
    df2['Year'] = 2016
    df3['Year'] = 2017
    df4['Year'] = 2018
    df5['Year'] = 2019
    combined_df = pd.concat([df1, df2, df3, df4, df5], ignore_index=True)
    ```

- **Trend Analysis**: Visualize trends in Happiness Score:
    ```python
    combined_df[combined_df['Country'] == 'India'].plot.line(x='Year', y='Happiness Score')
    combined_df[combined_df['Country'] == 'UnitedStates'].plot.line(x='Year', y='Happiness Score')
    ```

- **Regional Analysis**: Identify regions with low Economy (GDP per Capita):
    ```python
    df1[df1['Economy (GDP per Capita)'] < 0.5]['Region']
    ```

- **Correlation Identification**: Find highest correlations:
    ```python
    df1.corr()
    df2.corr()
    ```

## Result

The analysis provides insights into the happiness scores of countries, identifies trends over the years, and explores correlations between various factors.
