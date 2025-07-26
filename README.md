# Customer-Review-Analytics-with-Snowflake-Cortex
Building An AI-powered Customer Review Analytics Workflow With Snowflake Cortex and streamlit

# AI-powered Customer Review Analytics Dashboard with snowflake cortex

This project demonstrates an **end-to-end analytics pipeline** to process and analyze customer review data using **Snowflake Cortex's LLM capabilities** and visualize insights with **Streamlit** and **Altair**. It transforms unstructured text reviews from DOCX files into actionable sentiment trends, enabling data-driven business decisions.
Learn how to process and analyze customer review data using an LLM-powered data processing workflow with Snowflake Cortex followed by building a dashboard.

---

## 🚀 Overview

Learn how to build a complete analytics pipeline that:

* **Extracts and parses content** from DOCX files stored in Snowflake.
* **Reshapes unstructured text data** into a structured format via document parsing.
* **Applies Snowflake Cortex functions** for language translation, summarization, and sentiment analysis.
* **Creates interactive visualizations** with Streamlit and Altair.
* **Interprets sentiment analysis results** for business insights.

---

## ✨ What is Builded

builded a **customer review analytics dashboard** that processes unstructured text data and visualizes sentiment trends across products and time periods.

---

## 📋 Prerequisites
To get started, make sure you have:

* Access to a **Snowflake account**.
* Basic knowledge of **SQL and Python**.
* Familiarity with **data analysis concepts**.

---

## ⚙️ Setup & Data Processing

To get this project up and running, follow these detailed setup steps:

### 1. Download the Notebook

Download the main project notebook: `Avalanche-Customer-Review-Analytics.ipynb` from this GitHub repository. This notebook contains all the Python and SQL code you'll need.

### 2. Snowflake Environment Setup

Before running the notebook, configure your Snowflake environment:

* **Create Database and Schema:** Open a new SQL Worksheet in Snowsight and run the following commands to create your database and schema:

    ```sql
    CREATE DATABASE IF NOT EXISTS avalanche_db;
    CREATE SCHEMA IF NOT EXISTS avalanche_schema;
    ```

* **Create a Stage:** Create an internal stage where you'll upload the customer review DOCX files. Run this SQL command:

    ```sql
    CREATE STAGE IF NOT EXISTS avalanche_db.avalanche_schema.customer_reviews
      ENCRYPTION = (TYPE = 'SNOWFLAKE_SSE')
      DIRECTORY = (ENABLE = true);
    ```

    You should see a confirmation message indicating the stage was created successfully.

### 3. Upload Customer Review Data

* **Download Data:** Download the `customer_reviews_docx.zip` file, which contains 100 sample customer review DOCX files. Unzip this file to access the individual DOCX files.

* **Upload to Stage via Snowsight:**
    1.  In Snowsight, click on the **"Data"** icon from the left-hand menu.
    2.  Navigate through the database hierarchy: `AVALANCHE_DB` > `AVALANCHE_SCHEMA` > `Stages` > `CUSTOMER_REVIEWS`.
    3.  In the top-right corner of the "CUSTOMER_REVIEWS" stage panel, click the blue **"+ Files"** button.
    4.  Browse to the location where you unzipped `customer_reviews_docx.zip` and select all 100 DOCX files.
    5.  Confirm the upload. You'll see the files listed in the main panel once uploaded.

* **Verify Upload:** To confirm the files are successfully staged, open a new SQL Worksheet and run:

    ```sql
    ls @avalanche_db.avalanche_schema.customer_reviews;
    ```

    This command should list all the uploaded DOCX files.

### 4. Data Processing with Snowflake Cortex

With your data staged, you can now run the processing steps within the `Avalanche-Customer-Review-Analytics.ipynb` notebook: you can go to notebooks and import this ipynb file and run all the commands to see ouput

* **Extract Data from DOCX:** The notebook will use the `SNOWFLAKE.CORTEX.PARSE_DOCUMENT` function to extract content from your staged DOCX files.

* **Reshape & Analyze Data:**
    * SQL `REGEXP_SUBSTR` will be applied to extract specific fields like **PRODUCT**, **DATE**, and **CUSTOMER_REVIEW** from the raw text.
    * Snowflake Cortex LLM functions will then perform advanced text analysis:
        * **TRANSLATE**: Automatically translate reviews to English.
        * **SUMMARIZE**: Generate concise summaries of the reviews.
        * **SENTIMENT**: Calculate a numerical sentiment score for each review.
    * The processed SQL results will be converted into a **Pandas DataFrame** for further analysis and visualization in Python.

---

## 📊 Visualizations
The project's Streamlit application generates interactive charts using Altair to visualize sentiment trends from the processed data:

* **Daily Sentiment Scores:** A bar chart displaying sentiment scores over time, with bars colored green for positive and red for negative sentiment. Tooltips will show product and date details.
* **Product Sentiment Scores:** A bar chart showing the average sentiment scores for each product, using the same green/red coloring for sentiment. Tooltips will display product name and average sentiment.
* **Data Download:** A convenient button allows users to download the full processed dataset (including Product, Date, Summary, and Sentiment Score) as a CSV file.

---

## Outputs:

1st output-
<img width="1425" height="768" alt="3" src="https://github.com/user-attachments/assets/eb7c360a-998f-4a50-b72c-1d8f1fb762e1" />

2nd output-
<img width="1157" height="557" alt="2" src="https://github.com/user-attachments/assets/df45e94b-6b99-4484-9c23-b0ed3e0e46da" />

---
## 📚 References:

**Quickstart Guide:** For a detailed, step-by-step quickstart on this project, check out this link- 
 https://quickstarts.snowflake.com/guide/avalanche-customer-review-data-analytics

**Video Walkthrough:** To understand the project with a visual guide and video explanations, visit this link-

https://www.youtube.com/watch?v=jxHieQkG8BM&list=PLavJpcg8cl1HuMvwvqUdmXs0Wc_lUrHJn

---
