# Google Play Store App Analytics Dashboard

This project performs an in-depth analysis of Google Play Store app data, including app listings and user reviews, to uncover key trends, insights, and patterns. The analysis covers aspects like app categories, ratings, installs, revenue, sentiment analysis, and various time-gated dashboards for specific insights.

## Table of Contents
- [Project Overview](#project-overview)
- [Dataset](#dataset)
- [Methodology](#methodology)
- [Analysis and Visualizations](#analysis-and-visualizations)
- [Dashboards](#dashboards)


## Project Overview

This project aims to:
- Clean and preprocess raw Google Play Store app and user review data.
- Perform exploratory data analysis (EDA) to understand app distribution, user sentiments, and market trends.
- Identify top-performing categories, revenue generators, and app update patterns.
- Create interactive dashboards to present key findings.
- Implement advanced filtering and time-gating for specific analytical tasks.

## Dataset

The project utilizes two primary datasets:
1.  `Play Store Data.csv`: Contains comprehensive details about various apps available on the Google Play Store.
2.  `User Reviews.csv`: Contains user reviews for a subset of these apps, including translated reviews and sentiment scores.

## Methodology

1.  **Data Loading & Cleaning**: Loaded data using pandas. Handled missing values, converted data types (e.g., 'Installs', 'Price', 'Size' to numeric, 'Last Updated' to datetime), and removed duplicates.
2.  **Feature Engineering**: 
    - Created `Log_Installs` and `Log_Reviews` using logarithmic transformation.
    - Categorized app ratings into `Rating_Group` (e.g., 'Top rated app', 'Above average').
    - Calculated `Revenue` by multiplying `Price` and `Installs`.
    - Performed sentiment analysis on `Translated_Review` using `SentimentIntensityAnalyzer` (VADER) to derive `Sentiment_Score`.
    - Extracted `Year` from `Last Updated`.
3.  **Exploratory Data Analysis (EDA)**: Explored various aspects of the data through visualizations:
    - Top app categories.
    - Distribution of Free vs. Paid apps.
    - App rating distribution.
    - Sentiment distribution in user reviews.
    - Installs by category.
    - Updates per year trend.
    - Revenue by category.
    - Top genres.
    - Impact of last update on rating.
    - Rating for Paid vs. Free apps.
4.  **Interactive Dashboards**: Generated a main dashboard and several specific task-based dashboards using Plotly, saved as HTML files. These dashboards include custom styling and JavaScript for time-gated visibility for specific tasks.

## Analysis and Visualizations

The notebook generates several interactive plots to visualize different aspects of the data:

-   **Category Distribution**: Bar chart showing the top app categories.
-   **Type Analysis**: Pie chart illustrating the proportion of free vs. paid apps.
-   **Rating Distribution**: Histogram showing the spread of app ratings.
-   **Sentiment Distribution**: Bar chart displaying the sentiment (Positive, Negative, Neutral) of user reviews.
-   **Installs by Category**: Horizontal bar chart showing total installs across different categories.
-   **Updates Per Year**: Line plot showing the trend of app updates over the years.
-   **Revenue by Category**: Bar chart indicating which categories generate the most revenue.
-   **Top Genres**: Bar chart showcasing the most prevalent app genres.
-   **Impact of Last Update on Rating**: Scatter plot to analyze the correlation between app updates and ratings.
-   **Rating for Paid vs Free Apps**: Box plot comparing ratings between paid and free applications.
## Key findings

| Metric | Value |
|---|---|
| Cleaned app records | **8,892** (from 10,841 raw rows) |
| Categories | **33** |
| Free apps | **93.1%** |
| Most common category | **FAMILY** |
| Category with most installs | **GAME** |
| Median app rating | **4.3 / 5** |
| Apps with matched reviews | **1,020** |
| Total review rows processed | **64,295** |
## Dashboards

The project produces a comprehensive `dashboard.html` file that integrates all the main visualizations. Additionally, several specific tasks were implemented as separate dashboards with time-gated visibility:

-   **Task 1: Filtered Category Metrics** 
    -   **Description**: Compares average rating and total review count for top 10 app categories. Filters include January updates, rating >= 4.0, and size >= 10MB.
    -   **Visibility**: Only visible between 3 PM - 5 PM IST.

-   **Task 2: Global Installs by Category (Choropleth)** 
    -   **Description**: A choropleth map showing global install distribution for the top 5 categories (excluding those starting with A, C, G, S). Countries with over 1M installs are highlighted. Country data is added to met this limitation.
    -   **Visibility**: Only visible between 6 PM - 8 PM IST.

-   **Task 3: Avg Installs vs Avg Revenue (Dual-Axis)**
    -   **Description**: A dual-axis chart comparing average installs and average revenue for Free vs. Paid apps across the top 3 filtered categories.
    -   **Visibility**: Only visible between 1 PM - 2 PM IST.

-   **Task 4: Installs Trend with MoM Growth** 
    -   **Description**: Monthly install trends by category. Shaded regions indicate months where installs grew >20% Month-over-Month. Includes translated category names.
    -   **Visibility**: Only visible between 6 PM - 9 PM IST.

-   **Task 5: App Size vs Rating (Bubble Chart)** 
    -   **Description**: Bubble chart showing app size vs. rating, where bubble size represents installs. Filters include rating > 3.5, reviews > 500, installs > 50k, and review subjectivity > 0.5. The 'GAME' category is highlighted.
    -   **Visibility**: Only visible between 5 PM - 7 PM IST.

-   **Task 6: Cumulative Installs Over Time (Stacked Area)** 
    -   **Description**: Stacked area chart showing cumulative installs over time by category (only categories starting with T or P). Gold stars mark months with >25% MoM growth. Includes translated legend labels.
    -   **Visibility**: Only visible between 4 PM - 6 PM IST.


| # | Chart | Question it answers | Visible (IST) ||
|---|---|---|---|---|
| 1 | Grouped bar — avg rating & total reviews | Top categories for Jan-updated, rating ≥ 4, size ≥ 10MB apps | 3 PM – 5 PM |
| 2 | Choropleth — installs by country | Where are the top 5 categories (excl. A/C/G/S) installed most? | 6 PM – 8 PM |
| 3 | Dual-axis bar + line | Avg installs vs. avg revenue, Free vs. Paid | 1 PM – 2 PM |
| 4 | Shaded time series | Monthly install trend, >20% MoM growth highlighted | 6 PM – 9 PM | 
| 5 | Bubble chart | App size vs. rating, bubble size = installs | 5 PM – 7 PM | 
| 6 | Stacked area | Cumulative installs over time by category | 4 PM – 6 PM | 
