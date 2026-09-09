📚 Web Scraping & NLP Book Recommender

An end-to-end Python project that collects book data from a web scraping sandbox, transforms it into structured datasets, and builds a content-based recommendation system using Natural Language Processing (NLP).

Overview

This project demonstrates a practical workflow from web data collection to machine learning. Book information is extracted from Books to Scrape, a sandbox website designed for scraping practice.

The project currently contains two stages:

Web Scraping & Data Mining: Collect catalogue and product-level information, clean the data, and export it to CSV and Excel.
NLP Book Recommender: Transform book text using TF-IDF and recommend similar books using cosine similarity.

The current dataset contains 60 books. The next development stage is to scale the scraper to the full 1,000-book catalogue and evaluate how a larger candidate pool improves recommendation quality.

🛠️ Technologies
Technology	Purpose
Python	Core programming language
Requests	HTTP requests
BeautifulSoup	HTML parsing and data extraction
Pandas	Data cleaning and DataFrame operations
Regular Expressions	Extracting inventory quantities
Scikit-learn	TF-IDF and cosine similarity
Jupyter Notebook	Development and experimentation
OpenPyXL	Excel export
🔄 Project Workflow
Books to Scrape
       ↓
Catalogue Page Scraping
       ↓
Product URL Extraction
       ↓
Individual Product Pages
       ↓
Detailed Data & Descriptions
       ↓
Data Cleaning and Validation
       ↓
CSV / Excel Dataset
       ↓
Text Preprocessing
       ↓
TF-IDF Vectorization
       ↓
Cosine Similarity
       ↓
Top-N Book Recommendations
📊 Data Collected

The detailed dataset contains the following fields:

Field	Description
title	Book title
price	Book price
rating	Rating converted to a numeric value from 1–5
availability	Stock status
product_url	Individual product page URL
category	Book category
UPC	Unique Product Code
tax	Tax amount
reviews	Number of reviews
quantity	Available inventory quantity
description	Product description used for NLP

Dataset note: Books to Scrape contains fictional catalogue data. Prices and ratings are not real-world market or quality indicators, so they are not treated as reliable popularity or quality signals.

🕷️ Web Scraping
Catalogue Extraction

The scraper sends HTTP requests to catalogue pages and uses BeautifulSoup to identify repeating product containers. It extracts titles, prices, ratings, availability, and product URLs.

Pagination

Catalogue URLs are generated dynamically using Python loops:

page-1.html
page-2.html
page-3.html
...

This allows the same extraction logic to be applied across multiple pages without manually opening each one.

Individual Product Pages

Each product URL is visited to collect additional information from the product information table and description section.

Catalogue
    ├── Book A → Product details + description
    ├── Book B → Product details + description
    └── Book C → Product details + description

The detailed extraction includes category, UPC, tax, reviews, inventory quantity, and product description.

🧹 Data Cleaning

Raw website values are converted into analysis-ready formats.

Price conversion

£51.77 → 51.77

Rating conversion

One   → 1
Two   → 2
Three → 3
Four  → 4
Five  → 5

Inventory quantity extraction

In stock (22 available) → 22

Regular expressions are used to extract the numeric quantity. Tax values are converted to numeric types, review counts are converted to integers, and missing descriptions are handled before NLP processing.

🧠 NLP Book Recommender

The second notebook implements a content-based recommendation system that identifies books with similar textual content.

1. Text Feature Engineering

The title, category, and description are combined into a single text field:

df["combined_text"] = (
    df["title"].fillna("") + " " +
    df["category"].fillna("") + " " +
    df["description"].fillna("")
)

An experimental version also repeats the category field to give genre information more influence during vectorization.

2. TF-IDF Vectorization

Scikit-learn's TfidfVectorizer converts the combined text into numerical features while removing common English stop words.

tfidf = TfidfVectorizer(stop_words="english")
tfidf_matrix = tfidf.fit_transform(df["combined_text"])

The initial 60-book dataset produced a TF-IDF matrix of 60 × 3,349, representing 60 books and 3,349 text features.

3. Cosine Similarity

Cosine similarity is used to compare each book's TF-IDF vector with every other book.

similarity_matrix = cosine_similarity(tfidf_matrix)

The resulting similarity matrix has a shape of 60 × 60.

4. Recommendation Function

A reusable function accepts a book title and returns the top-N most similar books, excluding the selected book itself.

recommend_books(
    "Sapiens: A Brief History of Humankind",
    df,
    similarity_matrix
)

The output includes the recommended title, category, and similarity score.

Example Results

For A Light in the Attic, the initial model recommended several poetry books, including You can't bury them all: Poems, Shakespeare's Sonnets, and Slow States of Collapse: Poems.

For Sapiens: A Brief History of Humankind, the strongest initial recommendation was Unbound: How Eight Technologies Made Us Human, with a cosine similarity of approximately 0.1096.

These examples demonstrate that the model can identify relevant textual relationships, although the small and diverse dataset limits recommendation quality.

📁 Project Structure
web-scraping-data-mining/
├── 01_books_web_scraping.ipynb
├── 02_book_nlp_recommender.ipynb
├── books_scraped_detailed_v2.csv
├── books_scraped_detailed_v2.xlsx
└── README.md

The filenames above represent the current project structure. Additional folders may be introduced as the project grows.

🚀 How to Run
Install Dependencies
pip install requests beautifulsoup4 pandas openpyxl scikit-learn
Run the Scraping Notebook

Open 01_books_web_scraping.ipynb in Jupyter Notebook and execute the cells to collect and export the book dataset.

Run the NLP Notebook

Open 02_book_nlp_recommender.ipynb, load the exported CSV, and execute the preprocessing, TF-IDF, cosine similarity, and recommendation cells.

The NLP notebook uses the saved dataset, so the website does not need to be scraped again every time the recommender is tested.

✅ Current Progress

Send HTTP requests and parse HTML

Extract catalogue-level book information

Implement pagination

Extract individual product URLs

Scrape product-level details and descriptions

Clean prices, ratings, tax, reviews, and quantities

Export structured data to CSV and Excel

Build a 60-book NLP-ready dataset

Combine title, category, and description text

Implement TF-IDF vectorization

Calculate cosine similarity

Build a reusable top-N recommendation function

Test recommendations using different book titles

🚧 Next Steps

Scale the scraper to all 1,000 books

Refactor scraping logic into reusable functions

Add robust timeout, retry, and exception handling

Add request delays and progress tracking

Validate missing values, duplicates, and data types

Compare recommendation results before and after scaling

Experiment with category weighting and TF-IDF parameters

Evaluate recommendation relevance using manual or category-based metrics

Explore semantic embeddings as an alternative to TF-IDF

Develop a simple Streamlit recommendation interface

Store structured data in SQL for further analysis

💡 Skills Demonstrated

This project demonstrates practical experience in web scraping, HTML parsing, pagination, nested page extraction, Python data structures, regular expressions, data cleaning, ETL, Pandas, NLP feature engineering, TF-IDF, cosine similarity, and content-based recommendation systems.

It also demonstrates an iterative development process: starting with a small sample, validating the output, building a baseline model, and planning improvements based on observed limitations.

⚠️ Responsible Web Scraping

Books to Scrape is a sandbox website specifically designed for web scraping practice.

For real-world projects, automated data collection should consider website terms of service, robots.txt rules, API availability, rate limits, copyright, privacy, and applicable laws. Official APIs or permitted data exports should be used where appropriate.

🌍 Future Direction

The longer-term goal is to apply these data collection and analytics techniques to logistics, supply chain, and market intelligence use cases.

Potential applications include shipping schedule analysis, transit-time comparison, vessel and voyage data, trade-flow analysis, freight market intelligence, and supply-chain performance monitoring.

Web / API Data
       ↓
Data Collection
       ↓
Cleaning & Transformation
       ↓
SQL / Database
       ↓
Analytics & Machine Learning
       ↓
Visualization
       ↓
Business Insights

The book recommender serves as a learning project for building reliable data pipelines and applying analytical methods to unstructured text.
