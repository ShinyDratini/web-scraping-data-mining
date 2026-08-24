📚 Web Scraping & Data Mining with Python
Project Overview

This project demonstrates an end-to-end web scraping and data mining workflow using Python.

The scraper collects product information from Books to Scrape, a sandbox website specifically designed for web scraping practice. It extracts information from both catalogue pages and individual product pages, cleans and transforms the collected data using Pandas, and exports the final dataset to CSV/Excel for further analysis.

This project is part of my exploration of web scraping, data collection, ETL, and analytics automation using Python.

🎯 Project Objectives
Understand HTML webpage structures
Send HTTP requests using Python
Parse HTML using BeautifulSoup
Extract repeating product information
Automate data collection across multiple pages
Follow product URLs to collect detailed information
Clean and transform scraped data using Pandas
Convert raw text into analysis-ready data types
Export structured datasets to CSV and Excel
Build a foundation for future web data mining projects
🛠️ Technologies Used
Python
Requests – retrieving webpage HTML
BeautifulSoup – parsing and extracting HTML data
Pandas – data cleaning, transformation, and analysis
Regular Expressions (Regex) – extracting inventory quantities from text
Jupyter Notebook – development and documentation
OpenPyXL – Excel output
🔄 Data Pipeline
Catalogue Pages
      ↓
HTTP Requests
      ↓
BeautifulSoup
      ↓
Extract Basic Product Data
      ↓
Extract Product URLs
      ↓
Individual Product Pages
      ↓
Extract Detailed Product Data
      ↓
Data Cleaning & Transformation
      ↓
Pandas DataFrame
      ↓
CSV / Excel
📊 Data Collected

The scraper currently extracts information from both catalogue and individual product pages.

Field	Description
title	Book title
price	Listed book price
rating	Rating converted from text to 1–5
availability	Stock availability
product_url	URL of the individual product page
category	Book category
UPC	Unique Product Code
tax	Tax amount
reviews	Number of reviews
quantity	Available inventory quantity

This produces a structured dataset similar to:

Title	Price	Rating	Category	Tax	Reviews	Quantity
A Light in the Attic	51.77	3	Poetry	0.00	0	22
🕷️ Scraping Process
1. Catalogue Page Extraction

The scraper first identifies repeating product containers on each catalogue page.

From these elements, it extracts:

Title
Price
Rating
Availability
Product URL
2. Pagination

The scraper dynamically generates catalogue URLs rather than manually visiting each page.

page-1.html
page-2.html
page-3.html
...

This allows the same extraction logic to be applied across multiple catalogue pages.

3. Product Page Extraction

Each extracted product URL is then used to access the corresponding individual book page.

Additional information is collected from the product information table and breadcrumb navigation, including:

Category
UPC
Tax
Number of reviews
Inventory quantity

This introduces a second level of scraping:

Catalogue
   │
   ├── Book A ──→ Product Page A
   ├── Book B ──→ Product Page B
   ├── Book C ──→ Product Page C
   └── ...
🧹 Data Cleaning

Raw web data requires transformation before it can be analysed.

Price

Currency symbols are removed and prices are converted from strings to numeric values.

"£51.77" → 51.77
Rating

Ratings stored in HTML classes are mapped to numeric values.

One   → 1
Two   → 2
Three → 3
Four  → 4
Five  → 5
Inventory Quantity

Availability is originally stored as text:

In stock (22 available)

Regular expressions are used to extract the numerical quantity:

22
Tax and Reviews

Tax values are converted to numeric values and review counts are converted to integers to make the fields suitable for analysis.

📁 Project Structure
web-scraping-data-mining/
│
├── notebooks/
│   └── books_to_scrape.ipynb
│
├── data/
│   ├── books_scraped_basic.csv
│   ├── books_scraped_basic.xlsx
│   ├── books_scraped_detailed.csv
│   └── books_scraped_detailed.xlsx
│
├── README.md
├── requirements.txt
└── .gitignore
✅ Current Progress

Completed:

HTTP requests

HTML parsing with BeautifulSoup

Basic product extraction

Multi-page pagination

Price cleaning

Rating transformation

Pandas DataFrame creation

CSV/Excel export

Product URL extraction

Individual product page scraping

Category extraction

UPC extraction

Tax extraction

Review count extraction

Inventory quantity extraction

🚧 Next Steps

Scale scraper to the complete 1,000-book catalogue

Add HTTP status validation

Add timeout handling

Add exception handling for failed requests

Add request delays for responsible scraping

Add progress tracking

Detect missing or unexpected values

Remove and check duplicate records

Perform exploratory data analysis (EDA)

Create visualizations

Store collected data in SQL

Refactor scraper into reusable functions

💡 Skills Demonstrated

This project demonstrates practical experience with:

Web Data Collection

HTTP requests
HTML parsing
CSS/HTML element identification
Pagination
Nested page extraction

Python

Loops
Lists and dictionaries
String manipulation
Regular expressions
Error-aware data processing

Data Engineering

Data extraction
Data cleaning
Data type conversion
Structured dataset creation
CSV/Excel output
Basic ETL pipeline development

Data Analytics

Pandas DataFrames
Data validation
Preparing web data for downstream analysis
⚠️ Responsible Web Scraping

Books to Scrape is a sandbox website specifically designed for web scraping practice.

For real-world websites, automated data collection should only be performed where permitted and should take into consideration the website's terms of service, robots.txt rules, API availability, rate limits, copyright, privacy, and applicable laws.

Where an official API or permitted data export is available, it may be preferable to direct HTML scraping.

🚀 Future Direction

The techniques developed in this project can eventually be extended to more complex and permitted data collection use cases, particularly in logistics and supply chain analytics.

Potential future applications include analysing public data relating to:

Shipping schedules
Transit times
Vessel and voyage information
Trade flows
Freight market information
Supply chain performance

The longer-term objective is to build end-to-end pipelines that combine:

Web / API Data
      ↓
Data Collection
      ↓
Cleaning & Transformation
      ↓
SQL / Database
      ↓
Analytics
      ↓
Visualization
      ↓
Business Insights
