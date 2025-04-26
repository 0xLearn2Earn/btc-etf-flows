# 🟧 Bitcoin ETF Flow Data Scraper

This project automates the daily scraping of Bitcoin ETF inflow and outflow data from [farside.co.uk](https://farside.co.uk/bitcoin-etf-flow-all-data/) and stores the results in a `.csv` file. The purpose of this dataset is to provide a transparent view of institutional interest in Bitcoin ETFs and enable custom chart visualizations using tools like TradingView.

---

## 📈 What This Does

- Scrapes **daily Bitcoin ETF inflow/outflow** values (in millions USD)
- Stores each day's value in a version-controlled `.csv` file
- Automates the process with a scheduled cron job
- Enables data visualization in TradingView via `request.seed()` for custom indicators and strategies

---

## 🧠 Why This Is Useful

Understanding Bitcoin ETF flows provides insights into institutional buying/selling pressure. By overlaying this data on charts, traders can:

- Correlate ETF flows with BTC price action
- Spot accumulation/distribution patterns
- Compare Bitcoin ETF demand against other risk assets

---

## 🛠️ Tech Stack

- **Node.js**: core automation and scripting
- **Puppeteer**: headless browser used to scrape data
- **node-cron**: schedules the scraper to run once daily
- **moment-timezone**: ensures correct date formatting and timezone handling
- **csv-parser & json2csv**: used to manage and update the `.csv` file
- **GitHub**: stores the repo and daily-updated dataset

---

## 🗂️ Data File Location

All inflow/outflow data is stored in:
/Bitcoin-ETF-Flow-Data/data/BTC_ETF_INFLOWS_OUTFLOWS.csv


Each row includes:
- `Date` (YYYY-MM-DD)
- `Total Flow (in millions USD)`
- `Type` (Inflow / Outflow)

---

## 🔄 Automation Frequency

The script is scheduled to run **once per day**, ensuring a fresh data point is added every trading day. You can customize the schedule in `index.js` using the cron format if needed.

---

## 📊 Using with TradingView

To load this data into TradingView for use in custom indicators or visual overlays:

```pine
request.seed("https://raw.githubusercontent.com/0xLearn2Earn/btc-etf-flows/main/data/BTC_ETF_INFLOWS_OUTFLOWS.csv")

