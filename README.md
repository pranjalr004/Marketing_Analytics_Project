# Marketing Analytics Project

This project enriches customer review data with sentiment analysis to provide actionable insights into customer feedback and product satisfaction levels.

## Project Overview

The Marketing Analytics Project automates the process of extracting customer reviews from a SQL Server database and enriching them with sentiment analysis metrics. The results are stored in a structured CSV format for further analysis and reporting.

---

## File Descriptions

### 1. `customer_reviews_enrichment.py`
**Purpose:** Main Python script that performs data extraction, sentiment analysis, and data enrichment.

**Key Functionality:**
- **Data Extraction:** Fetches customer review data from the SQL Server database (PortfolioProject_MarketingAnalytics) using a database connection
- **Sentiment Analysis:** Uses VADER (Valence Aware Dictionary and sEntiment Reasoner) sentiment analyzer to calculate sentiment scores for each review text
- **Sentiment Categorization:** Categorizes reviews into sentiment categories (Positive, Negative, Mixed Positive, Mixed Negative, Neutral) based on both the sentiment score and the customer rating
- **Sentiment Bucketing:** Groups sentiment scores into predefined ranges (-1.0 to -0.5, -0.49 to 0.0, 0.0 to 0.49, 0.5 to 1.0) for aggregation and analysis
- **Data Export:** Outputs the enriched dataset to a CSV file with all original and newly calculated sentiment columns

**Dependencies:**
- pandas: Data manipulation and CSV operations
- nltk: Natural Language Toolkit for sentiment analysis
- pyodbc: SQL Server database connectivity
- sqlalchemy: SQL execution support

**Output:** Generates `fact_customer_reviews_with_sentiment.csv`

---

### 2. `fact_customer_reviews_with_sentiment.csv`
**Purpose:** Output data file containing customer reviews enriched with sentiment analysis metrics.

**Column Descriptions:**
- `ReviewID`: Unique identifier for each review
- `CustomerID`: Unique identifier for the customer who wrote the review
- `ProductID`: Unique identifier for the product being reviewed
- `ReviewDate`: Date when the review was posted
- `Rating`: Customer's numerical rating (typically 1-5 scale)
- `ReviewText`: Actual text content of the customer review
- `SentimentScore`: Calculated sentiment score from VADER analyzer (ranges from -1.0 to 1.0, where negative values indicate negative sentiment and positive values indicate positive sentiment)
- `SentimentCategory`: Classified sentiment category based on both sentiment score and rating (values: Positive, Negative, Mixed Positive, Mixed Negative, Neutral)
- `SentimentBucket`: Grouped sentiment score range for easier aggregation and analysis (values: -1.0 to -0.5, -0.49 to 0.0, 0.0 to 0.49, 0.5 to 1.0)

**Usage:** This CSV file can be imported into business intelligence tools, data warehouses, or further analyzed for marketing insights and decision-making.

---

### 3. `Queries/` (Directory)
**Purpose:** Reserved directory for storing SQL queries used in data extraction and analysis.

**Current Status:** Empty - intended for organizing database queries that support the enrichment process or for additional analytical queries.

**Intended Usage:**
- Store SQL scripts for fetching specific subsets of review data
- Archive queries used for exploratory data analysis
- Organize reusable queries for performance optimization

---

## How to Use

1. **Prerequisites:** Ensure you have the required Python packages installed:
   ```
   pip install pandas nltk pyodbc sqlalchemy
   ```

2. **Database Configuration:** Update the connection string in `customer_reviews_enrichment.py` with your SQL Server credentials and database details.

3. **Run the Script:** Execute the script to extract, enrich, and export the data:
   ```
   python customer_reviews_enrichment.py
   ```

4. **Output:** The enriched dataset will be saved to `fact_customer_reviews_with_sentiment.csv`

---

## Data Analysis Insights

The enriched dataset enables:
- **Sentiment Trend Analysis:** Track how customer sentiment changes over time
- **Product Performance:** Identify which products receive positive vs. negative feedback
- **Customer Satisfaction:** Correlate sentiment scores with customer ratings
- **Marketing Strategy:** Develop targeted marketing campaigns based on sentiment insights
- **Quality Improvement:** Identify common pain points from negative reviews
