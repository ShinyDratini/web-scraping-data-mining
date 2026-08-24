📚 Web Scraping & Data Mining with Python
Overview

This project demonstrates a web scraping and data mining workflow using Python.

The scraper collects book information from Books to Scrape, a sandbox website designed specifically for web scraping practice. It extracts information from catalogue pages and individual product pages, cleans the collected data, and exports the results into structured datasets for analysis.

The project serves as a foundation for applying web data collection techniques to future logistics, supply chain, and market intelligence projects.

🛠️ Technologies
Python
Requests
BeautifulSoup
Pandas
Regular Expressions (Regex)
Jupyter Notebook
OpenPyXL
🔄 Workflow
Catalogue Pages
      ↓
HTTP Request
      ↓
BeautifulSoup
      ↓
Extract Product Information
      ↓
Pagination
      ↓
Product URLs
      ↓
Individual Product Pages
      ↓
Detailed Data Extraction
      ↓
Data Cleaning
      ↓
Pandas DataFrame
      ↓
CSV / Excel
📊 Data Collected

The scraper currently collects:

Field	Description
title	Book title
price	Book price
rating	Rating from 1–5
availability	Stock status
product_url	Individual product page
category	Book category
UPC	Unique Product Code
tax	Tax amount
reviews	Number of reviews
quantity	Available inventory quantity
🕷️ Scraping Process
1. Catalogue Pages

The scraper first sends an HTTP request to each catalogue page.

BeautifulSoup is used to identify the repeating product containers and extract:

Title
Price
Rating
Availability
Product URL
2. Pagination

Rather than manually visiting each page, Python dynamically generates the page URLs.

page-1.html
page-2.html
page-3.html
...

This allows the same scraping logic to be applied across multiple pages.

3. Individual Product Pages

The scraper follows each extracted product URL to collect additional information.

Catalogue
    │
    ├── Book A → Product Page A
    ├── Book B → Product Page B
    ├── Book C → Product Page C
    └── ...

The individual pages provide:

Category
UPC
Tax
Number of reviews
Inventory quantity
🧹 Data Cleaning
Price

Prices are converted from text into numeric values.

£51.77 → 51.77
Rating

Ratings stored as HTML classes are converted into numerical values.

One   → 1
Two   → 2
Three → 3
Four  → 4
Five  → 5
Inventory Quantity

The website provides availability as text:

In stock (22 available)

Regex is used to extract the quantity:

22
Other Fields

Tax values are converted to numeric values and review counts are converted to integers so they can be used directly for analysis.

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

Send HTTP requests with Python

Parse HTML with BeautifulSoup

Extract product information

Handle multiple catalogue pages

Clean price data

Convert ratings to numerical values

Build Pandas DataFrames

Export data to CSV and Excel

Extract individual product URLs

Scrape individual product pages

Extract categories and UPCs

Extract tax and review information

Extract inventory quantities

🚧 Next Steps

Scale scraper to all 1,000 books

Add HTTP status checking

Add timeout and exception handling

Add request delays

Add progress tracking

Validate missing values and duplicates

Perform exploratory data analysis

Create data visualizations

Store scraped data in SQL

Refactor scraper into reusable functions

💡 Skills Demonstrated

This project demonstrates practical experience in:

Web scraping
HTML parsing
Pagination
Nested page extraction
Python loops and data structures
Regular expressions
Data cleaning
Data type conversion
Pandas
CSV and Excel output
Basic ETL pipeline development
⚠️ Responsible Web Scraping

Books to Scrape is a sandbox website specifically designed for web scraping practice.

For real-world projects, automated data collection should consider website terms of service, robots.txt rules, API availability, rate limits, copyright, privacy, and applicable laws.

Official APIs or permitted data exports should be used where appropriate.

🚀 Future Direction

The techniques developed in this project can eventually be applied to more complex data collection and analytics use cases, particularly in logistics and supply chain analytics.

Potential applications include:

Shipping schedule analysis
Transit-time comparison
Vessel and voyage data
Trade-flow analysis
Freight market intelligence
Supply-chain performance monitoring

The longer-term goal is to develop end-to-end pipelines:

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
