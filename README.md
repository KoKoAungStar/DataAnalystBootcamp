# 📊 Data Analyst Portfolio Projects

A collection of real-world data analysis projects covering **SQL**, **Python**, **Excel**, and **Tableau** — built as part of a structured Data Analyst Bootcamp.

---

## 📁 Projects Overview

| Project | Tools | Skills |
|---|---|---|
| COVID-19 Data Exploration | SQL (MS SQL Server) | Joins, CTEs, Window Functions, Views |
| Nashville Housing Data Cleaning | SQL (MS SQL Server) | Data Cleaning, SUBSTRING, PARSENAME, CTE |
| Amazon Price Tracker | Python (Jupyter Notebook) | Web Scraping, Automation, CSV, Email Alerts |
| Bike Buyers Dashboard | Excel | Pivot Tables, Dashboard, Data Analysis |
| AirBnB Analysis | Tableau | Data Visualization, Interactive Dashboard |

---

## 🦠 Project 1 — COVID-19 Data Exploration

**File:** `COVID Portfolio Project - Data Exploration.sql`
**Dataset:** `CovidDeaths.xlsx`, `CovidVaccinations.xlsx`

### What it does
Explores global COVID-19 data to uncover death rates, infection rates, and vaccination progress across countries and continents.

### SQL Skills Used
- `JOIN` — Linking Deaths and Vaccinations tables
- `CTE` (Common Table Expressions) — Rolling vaccination calculations
- `Temp Tables` — Storing intermediate results
- `Window Functions` — `OVER`, `PARTITION BY` for rolling totals
- `Aggregate Functions` — `SUM`, `MAX`, `COUNT`
- `Views` — Creating reusable query results for Tableau
- `Data Type Conversion` — `CAST`, `CONVERT`

### Key Analyses
```sql
-- Death percentage per country
(total_deaths / total_cases) * 100 AS DeathPercentage

-- Infection rate vs population
(total_cases / population) * 100 AS PercentPopulationInfected

-- Rolling vaccination count using Window Function
SUM(CONVERT(int, new_vaccinations))
OVER (PARTITION BY location ORDER BY date) AS RollingPeopleVaccinated
```

---

## 🏠 Project 2 — Nashville Housing Data Cleaning

**File:** `Data Cleaning Portfolio Project Queries.sql`
**Dataset:** `Nashville Housing Data for Data Cleaning.xlsx`

### What it does
Cleans a raw real estate dataset from Nashville, Tennessee — transforming messy, inconsistent data into a structured, analysis-ready format.

### SQL Skills Used
- **Standardize date formats** — `CONVERT(Date, SaleDate)`
- **Fill NULL values** — `ISNULL()` with self-JOIN on ParcelID
- **Split address columns** — `SUBSTRING`, `CHARINDEX` for street/city
- **Parse owner address** — `PARSENAME`, `REPLACE`
- **Standardize categorical values** — `CASE WHEN` (Y/N → Yes/No)
- **Remove duplicates** — `ROW_NUMBER()` with `PARTITION BY` CTE
- **Drop unused columns** — `ALTER TABLE DROP COLUMN`

### Cleaning Steps Summary

```
Raw Data                          →   Cleaned Data
-----------------------------         ----------------------------
SaleDate (datetime)               →   SaleDate (date only)
PropertyAddress (NULL gaps)       →   Filled via ParcelID match
"123 Main St, Nashville"          →   Address | City (split)
SoldAsVacant = 'Y' / 'N'         →   'Yes' / 'No'
Duplicate rows                    →   Removed with ROW_NUMBER CTE
Unused columns (4)                →   Dropped from table
```

---

## 🛒 Project 3 — Amazon Price Tracker (Web Scraper)

**File:** `Amazon Web Scraper Project.ipynb`

### What it does
Automatically tracks the price of a product on Amazon over time, saves the data to CSV, and sends an email alert when the price drops below a set threshold.

### Python Libraries Used
| Library | Purpose |
|---|---|
| `BeautifulSoup` | Parse HTML from Amazon product page |
| `requests` | Send HTTP requests with custom headers |
| `csv` | Read/write price history to CSV file |
| `datetime` | Timestamp each price check |
| `smtplib` | Send automated email price alerts |
| `time` | Schedule repeated checks |

### How It Works

```
1. Connect to Amazon product URL
         ↓
2. Parse HTML → Extract title + price
         ↓
3. Clean data (strip whitespace, remove $)
         ↓
4. Append to CSV with today's date
         ↓
5. Check: price < target?
         ↓
6. Yes → Send email alert via smtplib
         ↓
7. Wait (time.sleep) → Repeat automatically
```

### Key Code Concepts
```python
# Web scraping with headers to mimic browser
soup = BeautifulSoup(page.content, "html.parser")
title = soup.find(id='productTitle').get_text().strip()
price = soup.find(id='priceblock_ourprice').get_text().strip()

# Auto-repeat every 24 hours
while True:
    check_price()
    time.sleep(86400)
```

---

## 🚲 Project 4 — Bike Buyers Dashboard (Excel)

**File:** `Excel Project.xlsx`
**Dataset:** 1,026 rows × 14 columns

### What it does
Analyzes a dataset of potential bike buyers to understand purchasing patterns based on income, gender, commute distance, age, and region.

### Dataset Columns
`ID`, `Marital Status`, `Gender`, `Income`, `Children`, `Education`, `Occupation`, `Home Owner`, `Cars`, `Commute Distance`, `Region`, `Age`, `Age Bracket`, `Purchased Bike`

### Sheets
| Sheet | Purpose |
|---|---|
| `bike_buyers` | Raw + cleaned data |
| `Pivot Table` | Income analysis by gender and purchase decision |
| `Dashboard` | Visual summary for decision making |

### Key Insight (from Pivot Table)
```
Average Income — Purchased Bike = Yes vs No

              No          Yes
Female:    $54,885     $59,259
Male:      $59,431     $61,300

→ Higher income correlates with bike purchase across both genders
```

---

## 📈 Project 5 — AirBnB Data Analysis (Tableau)

**Live Dashboard:** [View on Tableau Public](https://public.tableau.com/app/profile/ko.ko.aung/viz/AirBnBFullProject_17241921330310/Dashboard1?publish=yes)

### What it does
Analyzes AirBnB listing data to uncover pricing trends, revenue patterns, and location-based insights — published as an interactive Tableau dashboard.

### Visualizations Include
- Average price by location/zip code
- Revenue trends over time
- Pricing by number of bedrooms
- Interactive filters for exploration

---

## 🛠️ Tools & Technologies

| Category | Tools |
|---|---|
| Database | Microsoft SQL Server (SSMS) |
| Language | Python 3, SQL |
| Notebook | Jupyter Notebook |
| Spreadsheet | Microsoft Excel |
| Visualization | Tableau Public |
| Libraries | BeautifulSoup, Requests, Pandas, CSV, Smtplib |

---

## 📂 Repository Structure

```
DataAnalystBootcamp/
│
├── COVID Portfolio Project - Data Exploration.sql
├── CovidDeaths.xlsx
├── CovidVaccinations.xlsx
│
├── Data Cleaning Portfolio Project Queries.sql
├── Nashville Housing Data for Data Cleaning.xlsx
│
├── Amazon Web Scraper Project.ipynb
│
├── Excel Project.xlsx
│
└── Tableau Data analysis Project (link inside)
```

---

## 🚀 How to Run Each Project

### SQL Projects
1. Install [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms)
2. Create a database named `PortfolioProject`
3. Import the `.xlsx` datasets as tables (`CovidDeaths`, `CovidVaccinations`, `NashvilleHousing`)
4. Open and run the `.sql` files

### Python Web Scraper
```bash
pip install beautifulsoup4 requests pandas

# Open Jupyter Notebook
jupyter notebook "Amazon Web Scraper Project.ipynb"
```

### Excel Dashboard
Open `Excel Project.xlsx` in Microsoft Excel — all pivot tables and dashboard are pre-built.

### Tableau Dashboard
View live at: [Tableau Public Link](https://public.tableau.com/app/profile/ko.ko.aung/viz/AirBnBFullProject_17241921330310/Dashboard1?publish=yes)

---

## 👨‍💻 Developer

**Ko Ko Aung**
- GitHub: [KoKoAungStar](https://github.com/KoKoAungStar)
- LinkedIn: [ko-ko-aung-dev](https://linkedin.com/in/ko-ko-aung-dev)
- Tableau Public: [Profile](https://public.tableau.com/app/profile/ko.ko.aung)

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
