📚 Web Scraping & Data Mining with Python
Project Overview

This project demonstrates a web scraping and data mining workflow using Python. The objective is to extract product information from Books to Scrape, a website specifically designed for practising web scraping.

The project collects unstructured information from HTML pages, transforms it into a structured dataset, cleans the extracted data, and exports the results for further analysis.

This project is part of my exploration of web scraping, data collection, and analytics automation using Python.

🎯 Project Objectives
Understand the structure of HTML webpages
Send HTTP requests using Python
Parse HTML using BeautifulSoup
Identify and extract repeating product information
Automate data collection across multiple pages
Clean and transform scraped data using Pandas
Store the results in structured formats such as CSV and Excel
Build a foundation for future web data mining and analytics projects
🛠️ Technologies Used
Python
Requests – retrieving webpage HTML
BeautifulSoup – parsing and extracting information from HTML
Pandas – data cleaning, transformation, and analysis
Jupyter Notebook – development and documentation
OpenPyXL – Excel output
🔄 Data Pipeline
Website
   ↓
HTTP Request
   ↓
HTML
   ↓
BeautifulSoup
   ↓
Data Extraction
   ↓
Pagination
   ↓
Data Cleaning
   ↓
Pandas DataFrame
   ↓
CSV / Excel
📊 Data Collected

The scraper currently extracts the following information for each book:

Field	Description
title	Book title
price	Listed book price
rating	Book rating from 1–5
availability	Current stock availability

Example output:

Title	Price	Rating	Availability
A Light in the Attic	51.77	3	In stock
Tipping the Velvet	53.74	1	In stock
Soumission	50.10	1	In stock
Sharp Objects	47.82	4	In stock
Sapiens: A Brief History of Humankind	54.23	5	In stock
🧹 Data Cleaning

The raw website data requires several transformations before analysis.

Price

The original price is extracted as text containing a currency symbol.

£51.77

It is converted into a numeric value:

51.77

This allows calculations such as average, minimum, and maximum price.

Rating

Ratings on the website are stored within HTML classes:

One
Two
Three
Four
Five

These values are mapped to numerical ratings:

One   → 1
Two   → 2
Three → 3
Four  → 4
Five  → 5
Availability

Extra whitespace and line breaks are removed from the availability field to produce a clean value such as:

In stock
🔁 Pagination

Instead of manually scraping individual webpages, the scraper dynamically generates page URLs and loops through multiple pages.

Example:

page-1.html
page-2.html
page-3.html
...

The current implementation has successfully extracted data across multiple pages and can be extended to scrape the full practice catalogue.

📁 Project Structure
web-scraping-data-mining/
│
├── notebooks/
│   └── books_to_scrape.ipynb
│
├── data/
│   ├── books_scraped.csv
│   └── books_scraped.xlsx
│
├── README.md
├── requirements.txt
└── .gitignore
📈 Planned Improvements

Future development of this project will include:

Scrape the complete 1,000-book catalogue

Extract product categories

Extract individual product URLs

Collect additional information from individual product pages

Add HTTP error handling

Handle missing or unexpected values

Add delays and responsible request handling

Perform exploratory data analysis

Create data visualizations

Store scraped data in SQL

Develop a reusable scraping pipeline

💡 Skills Demonstrated

This project demonstrates practical experience with:

Web scraping
HTML parsing
Python loops
Pagination
Data extraction
Data cleaning
Data type conversion
Pandas DataFrames
Data validation
CSV and Excel export
Basic ETL workflow development
⚠️ Responsible Web Scraping

Books to Scrape is a sandbox website specifically created for web scraping practice.

For real-world websites, automated data collection should only be performed where permitted and should take into consideration the website's terms of service, robots.txt rules, API availability, rate limits, copyright, privacy, and applicable laws.

Where an official API or data export is available, it may be preferable to direct HTML scraping.

🚀 Future Direction

The techniques developed in this project can be extended to more complex data collection use cases.

A future goal is to apply these skills to logistics and supply chain analytics, including permitted collection and analysis of public information such as shipping schedules, trade data, transit times, vessel information, and other market intelligence.

The longer-term objective is to combine:

Data Collection
      ↓
Data Engineering
      ↓
SQL / Database
      ↓
Data Analysis
      ↓
Visualization
      ↓
Business Insights

to develop end-to-end data analytics solutions.
