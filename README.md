# stock-revenue-analysis-dashboard
# 📈 Historical Stock & Revenue Dashboard: Tesla & GameStop

An end-to-end financial data engineering and visualization project analyzing historical stock price trends against quarterly corporate revenues for **Tesla (TSLA)** and **GameStop (GME)**.

---

## 📌 Project Overview

Stock market performance is often driven by corporate fundamentals, speculative retail momentum, and macroeconomic shifts. This project investigates the historical relationship between stock price movements and actual quarterly revenue by:
1. Programmatically retrieving historical equity market data via financial APIs.
2. Web-scraping and parsing unstructured corporate revenue statements from web tables.
3. Cleansing and normalizing heterogeneous monetary figures.
4. Building multi-panel interactive dashboards to evaluate market dynamics through June 2021 (capturing notable market events such as the 2020–2021 EV rally and the 2021 GameStop short squeeze).

---

## 🛠 Tech Stack & Tools

* **Language:** Python 3.x
* **Data Retrieval & Scraping:**
  * [`yfinance`](https://github.com/ranaroussi/yfinance) — Historical stock pricing (OHLCV) and dividend adjustments
  * [`requests`](https://requests.readthedocs.io/) — HTTP GET transactions and webpage source acquisition
  * [`BeautifulSoup4`](https://www.crummy.com/software/BeautifulSoup/) & `html5lib` / `html.parser` — DOM navigation and HTML table parsing
* **Data Processing & Transformation:**
  * [`pandas`](https://pandas.pydata.org/) — Relational data manipulation, type coercion, and cleaning
* **Visualization:**
  * [`plotly`](https://plotly.com/python/) — Interactive dual-axis / multi-panel financial graphing

---

## 🚀 Key Deliverables & Pipeline

### 1. Stock Market Data Ingestion (`yfinance`)
* Initialized `Ticker` objects for Tesla (`TSLA`) and GameStop (`GME`).
* Extracted maximum available daily historical price data (`period="max"`).
* Flattened the DataFrame hierarchy and normalized timestamp indices with `.reset_index()`.

### 2. Web Scraping & DOM Traversal (`requests` + `BeautifulSoup`)
* Executed HTTP GET requests to retrieve archived quarterly financial statements.
* Traversed HTML tree nodes (`<table>`, `<tbody>`, `<tr>`, `<td>`) to isolate target tables:
  * Tesla Quarterly Revenue
  * GameStop Quarterly Revenue
* Loaded raw strings into structured Pandas DataFrames.

### 3. Data Cleaning & Transformation
* Removed non-numeric characters, currency markers (`$`), and thousand delimiters (`,`) using regex string replacement.
* Handled missing / null entries (`.dropna()`) and eliminated empty string records.
* Formatted date sequences into structured chronological timelines.

### 4. Interactive Dashboard Generation (`make_graph`)
* Produced synchronized dual-panel subplots:
  * **Top Subplot:** Historical Share Price over time with interactive range sliders.
  * **Bottom Subplot:** Quarterly Revenue over time.
* Standardized timeline windows up to **June 2021** to compare revenue growth with market capitalization surges.

---

## 📂 Repository Structure

```text
├── Revenue Data and Building a Dashboard.ipynb   # Main Jupyter Notebook with full implementation
├── README.md                                     # Project documentation and summary
└── requirements.txt                              # Python environment dependencies
