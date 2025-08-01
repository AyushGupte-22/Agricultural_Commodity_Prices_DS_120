# Agricultural Commodity Prices EDA - Nagpur District (2016–2024)

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Jupyter Notebook](https://img.shields.io/badge/Jupyter-Notebook-orange)
![License](https://img.shields.io/badge/License-MIT-green)

## Project Overview

This repository contains an **Exploratory Data Analysis (EDA)** of agricultural commodity prices in the Nagpur district, Maharashtra, India, covering 2016–2024. The analysis is part of a Data Science course (TE7253) by Ayush Gupte (PRN: 22070521120, Batch 2022–26). The primary objective is to dissect the `Agriculture_Crop_Dataset.csv` to identify key drivers of commodity prices, validate data quality, and lay the groundwork for predictive modeling of the `Modal_Price` (the most frequent transaction price).

The EDA leverages Python libraries (`Pandas`, `Matplotlib`, `Seaborn`) to perform univariate, bivariate, and multivariate analyses, revealing price distributions, market and commodity dominance, temporal patterns, and feature relationships. Key findings include a right-skewed `Modal_Price`, significant trade volume in Nagpur’s main market, dominance of Soyabean and Tomato, and strong seasonal price fluctuations.

## Dataset Description

The dataset, sourced from [data.gov.in](https://www.data.gov.in/resource/variety-wise-daily-market-prices-data-commodity), contains **406,460 records** of daily agricultural commodity transactions from Agricultural Produce Market Committees (APMCs) in Nagpur. It spans 2016–2024 and includes the following schema:

- **Identifier Variables (Categorical)**:
  - `Market`: The marketplace location (e.g., Nagpur, Kamthi).
  - `Commodity`: The agricultural product (e.g., Soyabean, Tomato).
  - `Variety`: Sub-category of the commodity.
  - `Grade`: Quality classification (e.g., FAQ - Fair Average Quality).
- **Temporal Variable**:
  - `Arrival_Date`: Date of transaction (string, converted to datetime).
- **Quantitative Variables (Numerical)**:
  - `Min_Price`: Minimum transaction price (INR).
  - `Max_Price`: Maximum transaction price (INR).
  - `Modal_Price`: Most frequent transaction price (target variable, INR).
  - `Commodity_Code`: Numerical identifier for the commodity.

The dataset is complete with no missing values, as verified by `df.isnull().sum()`.

## EDA Methodology

The EDA, implemented in `train.ipynb`, follows a systematic approach to explore the dataset:

1. **Data Integrity and Preparation**:
   - Verified no missing values, ensuring high data quality.
   - Converted `Arrival_Date` to datetime using `pd.to_datetime(df['Arrival_Date'], format='%d/%m/%Y')` for time-series analysis.
   - Engineered temporal features (`Year`, `Month`, `Day`) for trend and seasonality analysis.

2. **Visualizations** (from `train.ipynb` and report):
   - **Modal_Price Distribution (Cell 14, intended)**: Sets up a histogram and boxplot to analyze `Modal_Price` distribution, revealing right-skewness and outliers (mean 2527.87 INR, max 100,000 INR).
   - **Correlation Heatmap (Cell 15)**: Visualizes Pearson correlations among numerical features (`Min_Price`, `Max_Price`, `Modal_Price`, `Commodity_Code`, `Year`, `Month`, `Day`) using `sns.heatmap`, highlighting strong price feature correlations (e.g., 0.95).
   - **Categorical Feature Bar Plots (hypothetical, inspired by report)**: Plots top 10 `Market`, `Commodity`, and `Grade` frequencies using `sns.barplot`, identifying dominant categories (e.g., Nagpur market, Soyabean, FAQ grade).
   - **Time-Series Line Plots (hypothetical, inspired by report)**: Plots average `Modal_Price` by `Year` and `Month` using `matplotlib.pyplot.plot`, revealing upward trends and July price peaks.

## Key Findings

- **Data Integrity**: The dataset is complete, with no missing values, ensuring reliable analysis.
- **Price Distribution**: `Modal_Price` is right-skewed, with a compressed interquartile range and outliers (e.g., high-value spices), suggesting log-transformation for modeling.
- **Market and Commodity Dominance**: Nagpur is the primary trading hub, with Soyabean and Tomato as the most traded commodities. FAQ grade dominates, indicating standardized pricing.
- **Temporal Patterns**: Prices show an upward trend (likely due to inflation) and seasonal peaks in July (pre-Kharif harvest scarcity), with drops post-harvest.
- **Feature Relationships**: Strong correlations among `Min_Price`, `Max_Price`, and `Modal_Price` (e.g., 0.95) confirm data consistency, while weak correlations with `Year` (0.29) and other features suggest complex, non-linear price drivers.

## Installation and Setup

To run the `train.ipynb` notebook, follow these steps:

### Prerequisites
- Python 3.8+
- Jupyter Notebook
- Required libraries: `pandas`, `numpy`, `matplotlib`, `seaborn`

### Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/AyushGupte-22/Agricultural_Commodity_Prices_DS_120.git
   cd Agricultural_Commodity_Prices_DS_120
   ```
2. Install dependencies:
   ```bash
   pip install pandas numpy matplotlib seaborn
   ```
3. Ensure the dataset (`Agriculture_Crop_Dataset.csv`) is in the repository’s root directory.

### Running the Notebook
1. Launch Jupyter Notebook:
   ```bash
   jupyter notebook
   ```
2. Open `train.ipynb` and run all cells. Ensure the Python kernel supports the required libraries.

## Usage

The `train.ipynb` notebook is structured as follows:
- **Data Loading and Cleaning**: Loads the dataset, verifies integrity, and converts `Arrival_Date` to datetime.
- **Feature Engineering**: Extracts `Year`, `Month`, and `Day` from `Arrival_Date`.
- **EDA**: Includes visualizations for `Modal_Price` distribution (incomplete), correlation heatmap, and placeholders for categorical and time-series plots.
- **Next Steps**: Recommendations for feature engineering (e.g., encoding categorical variables), data transformation (e.g., log-transforming `Modal_Price`), and model development (e.g., Random Forest).

To extend the EDA:
1. Implement the hypothetical bar plots for `Market`, `Commodity`, and `Grade` (see report Section 4.2).
2. Add time-series plots for `Modal_Price` by `Year` and `Month` (see report Section 4.4).
3. Explore bivariate boxplots for `Modal_Price` vs. `Market` and `Commodity` (report Section 4.3).

## Conclusion

This EDA validates the dataset’s suitability for predicting `Modal_Price`, emphasizing `Market`, `Commodity`, `Grade`, and temporal features as key predictors. The findings provide actionable insights:
- **Farmers**: Optimize selling in July to leverage seasonal price peaks.
- **Traders**: Target Nagpur’s main market for high liquidity.
- **Policymakers**: Address July scarcity to stabilize prices.

Recommended next steps include feature engineering (e.g., encoding categorical variables), log-transforming `Modal_Price`, and testing regression models (e.g., Linear Regression, Random Forest) for accurate price forecasting.

## References

- **Dataset**: [Variety-wise Daily Market Prices Data](https://www.data.gov.in/resource/variety-wise-daily-market-prices-data-commodity)
- **GitHub Repository**: [AyushGupte-22/Agricultural_Commodity_Prices_DS_120](https://github.com/AyushGupte-22/Agricultural_Commodity_Prices_DS_120)
- **Report**: `22070521120_CA1_EDA.docx` (Ayush Gupte, TE7253, 2025)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact

For questions or contributions, contact Ayush Gupte via [GitHub](https://github.com/AyushGupte-22).

---
***Generated by Ayush Gupte, PRN: 22070521120, Batch 2022–26, for Data Science course.***
