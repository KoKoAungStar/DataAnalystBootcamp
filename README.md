# Data Analyst Portfolio Projects

A collection of real-world data analysis projects covering **SQL**, **Python**, **Excel**, and **Tableau**.

[![View on Tableau Public](https://img.shields.io/badge/Tableau-View%20Live%20Dashboard-1F4E79?style=for-the-badge&logo=tableau&logoColor=white)](https://public.tableau.com/app/profile/ko.ko.aung/viz/AirBnBFullProject_17241921330310/Dashboard1?publish=yes)

---

## Projects Overview

| # | Project | Tools |
|---|---|---|
| 1 | COVID-19 Data Exploration | SQL (MS SQL Server) |
| 2 | Nashville Housing Data Cleaning | SQL (MS SQL Server) |
| 3 | Amazon Price Tracker | Python, Jupyter Notebook |
| 4 | Bike Buyers Dashboard | Excel |
| 5 | AirBnB Analysis | Tableau |

---

## How to Run

**SQL Projects (1, 2)**
1. Install [SSMS](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms)
2. Create database `PortfolioProject`, import the `.xlsx` files as tables
3. Open and run the `.sql` files

**Python Web Scraper (3)**
```bash
pip install beautifulsoup4 requests pandas
jupyter notebook "Amazon Web Scraper Project.ipynb"
```

**Excel Dashboard (4)**
Open `Excel Project.xlsx` — pivot tables and dashboard are pre-built.

**Tableau Dashboard (5)**
[View live →](https://public.tableau.com/app/profile/ko.ko.aung/viz/AirBnBFullProject_17241921330310/Dashboard1?publish=yes)

---

## Project 1 — COVID-19 Data Exploration

**Files:** `COVID Portfolio Project - Data Exploration.sql`, `CovidDeaths.xlsx`, `CovidVaccinations.xlsx`

Explores global COVID-19 data to uncover death rates, infection rates, and vaccination progress across countries and continents.

**Skills:** Joins, CTEs, Temp Tables, Window Functions, Views, Type Conversion

```sql
-- Death percentage per country
(total_deaths / total_cases) * 100 AS DeathPercentage

-- Rolling vaccination count
SUM(CONVERT(int, new_vaccinations))
OVER (PARTITION BY location ORDER BY date) AS RollingPeopleVaccinated
```

---

## Project 2 — Nashville Housing Data Cleaning

**Files:** `Data Cleaning Portfolio Project Queries.sql`, `Nashville Housing Data for Data Cleaning.xlsx`

Cleans a raw real estate dataset — transforming inconsistent data into a structured, analysis-ready format.

**Skills:** Date standardization, NULL filling, Address splitting, Duplicate removal, Column drops

```
Raw Data                    →   Cleaned Data
SaleDate (datetime)         →   SaleDate (date only)
PropertyAddress (NULLs)     →   Filled via ParcelID match
SoldAsVacant = 'Y' / 'N'   →   'Yes' / 'No'
Duplicate rows              →   Removed with ROW_NUMBER CTE
```

---

## Project 3 — Amazon Price Tracker

**File:** `Amazon Web Scraper Project.ipynb`

Tracks an Amazon product price over time, logs to CSV, and sends an email alert when price drops below a threshold.

**Libraries:** `BeautifulSoup`, `requests`, `csv`, `datetime`, `smtplib`, `time`

```python
soup = BeautifulSoup(page.content, "html.parser")
title = soup.find(id='productTitle').get_text().strip()

while True:
    check_price()
    time.sleep(86400)  # repeat every 24 hours
```

---

## Project 4 — Bike Buyers Dashboard

**File:** `Excel Project.xlsx` — 1,026 rows × 14 columns

Analyzes purchasing patterns based on income, gender, commute distance, and region.

```
Average Income — Purchased Bike: Yes vs No

              No          Yes
Female:    $54,885     $59,259
Male:      $59,431     $61,300

→ Higher income correlates with bike purchase across both genders
```

---

## Project 5 — AirBnB Data Analysis (Tableau)

Analyzes AirBnB listing data to uncover pricing trends, revenue patterns, and location-based insights.

**Visualizations:** Price by zip code · Revenue over time · Pricing by bedrooms · Interactive filters

### Dashboard

[![View on Tableau Public](https://img.shields.io/badge/Tableau-View%20Live%20Dashboard-1F4E79?style=for-the-badge&logo=tableau&logoColor=white)](https://public.tableau.com/app/profile/ko.ko.aung/viz/AirBnBFullProject_17241921330310/Dashboard1?publish=yes)

---

## Developer

**Ko Ko Aung**
- GitHub: [KoKoAungStar](https://github.com/KoKoAungStar)
- LinkedIn: [ko-ko-aung-dev](https://linkedin.com/in/ko-ko-aung-dev)
- Tableau Public: [Profile](https://public.tableau.com/app/profile/ko.ko.aung)

---

*MIT License*
