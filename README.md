<div align="center">

# ☀️ Tracker Market Intelligence

### A dashboard for the solar tracker market that updates itself every day 🔆📈

![Status](https://img.shields.io/badge/status-in%20development-orange)
![Python](https://img.shields.io/badge/python-3.10%2B-blue)
![Dash](https://img.shields.io/badge/Dash%20%2B%20Plotly-dashboard-yellow)
![Data](https://img.shields.io/badge/data-updated%20daily-brightgreen)

🎓 *Desarrollo de Aplicaciones para la Visualización de Datos* · Universidad Pontificia Comillas (ICAI)

</div>

---

> 🚧 **Status: in development.** A first working version exists: the daily data is live ⚡, while the market model series use illustrative values until the real data is uploaded.

---

## 🌞 Motivation

This project comes out of my internship in strategy consulting, on a project for a solar tracker manufacturer. My part of the work is the market: how much solar is being installed in each country and segment, how much of it uses trackers, how large the retrofit opportunity is, and how solar and tracker prices differ across regions and why. Today all of this sits in a large Excel model fed by hand from industry reports, databases and expert knowledge. 📊

### 🔄 What is a solar tracker?

A solar tracker rotates the panels so they follow the sun during the day ☀️➡️🌇. Compared with a fixed-tilt structure it produces roughly **15–25% more energy**, which is why it has become the standard choice for large ground-mounted plants in the United States, the Middle East and Latin America.

The market is growing quickly: **134 GWdc** of trackers were shipped worldwide in 2025, **19% more** than in 2024 (Wood Mackenzie). But where that growth happens is shifting:

- 🇺🇸 The US passed **40 GWdc** for the first time
- 🇸🇦 Saudi Arabia has overtaken Spain as the **third-largest market**
- 🌍 Africa is **growing fastest**

### 🎯 Why it matters

For a manufacturer, a country is not attractive just because it installs a lot of solar. Most residential and commercial systems sit on rooftops 🏠 and never use a tracker, so what matters is:

- 🏭 the **utility-scale** segment
- 🔆 the share of it built with **trackers**
- 🔧 the installed base of older fixed-tilt plants that could be **retrofitted**
- 💶 the **price** a tracker can be sold at in that region

Those prices vary widely between regions, and the reasons behind the gaps (module prices, tariffs, steel, freight, labour, local content rules) shift over time.

Providers such as Wood Mackenzie or BloombergNEF publish this kind of information, but their reports are expensive 💸, come out once or twice a year and arrive as PDFs or spreadsheets rather than as a tool that can be filtered and compared. Much of the underlying data is public and updated often, but it is scattered across many sources.

### ✨ The goal

Turn a manual and static market analysis into an interactive application that:

- ⚡ **updates itself every day**
- 📏 measures the **real size of the tracker market** in each region (utility-scale additions × attach rate + retrofit demand)
- 🔍 explains **why prices differ** between regions
- 🎛️ lets the user **change the main assumptions**
- 🔮 adds a **forecasting layer** to show where each region is likely to go

> 🔒 **Confidentiality.** The manufacturer is never named, and the series that come from the internal model (such as attach rates or retrofit volumes by country) are shown with illustrative values built from public figures. The application accepts an Excel or CSV upload with the real data, so anyone who has it can run the same analysis.

---

## 🗺️ Strategic vision

### 🌐 Scope

The solar market **outside China**, where Western tracker manufacturers compete, grouped into four regions:

| 🇺🇸 North America | 🇪🇺 Europe | 🌎 Latin America | 🌍 Rest of World |
|:---:|:---:|:---:|:---:|

Every chart can be read at country or regional level and split by segment:

| 🏠 Residential | 🏢 Commercial & Industrial (C&I) | 🏭 Utility-scale |
|:---:|:---:|:---:|
| Rooftops, no trackers | Mostly rooftops | **Largest segment, where trackers are used** |

### 🤝 A support tool, not a replacement

The application is not meant to replace the team's market model. It works **alongside it**, keeps it up to date and makes the day-to-day analysis easier.

### 👥 Users

Strategy and business development teams at tracker manufacturers, and consultants working on projects in the sector.

- ⏱️ **Time saved:** nobody has to look up and paste every new figure
- ⚖️ **Consistency:** every region is measured the same way
- 🔎 **Traceability:** the source of each number is visible

### 🧩 Content

| ❓ Question | 📊 What the application shows |
|---|---|
| ☀️ How much solar is being installed? | PV additions by country and region, split by residential, C&I and utility-scale |
| 🔆 How much of it uses trackers? | Tracker attach rates by region |
| 🔧 How large is the retrofit opportunity? | Retrofit demand from older fixed-tilt plants, and new build vs retrofit |
| 💶 Why do prices differ between regions? | Solar and tracker prices by region and the drivers of the gaps; historical evolution of prices with trackers; key drivers of tracker costs |
| 🔮 How will it evolve? | An integrated view, past and projected by region, combining everything into the tracker market in GW and in value |

The user will be able to filter by region and segment 🎛️ and adjust the main assumptions, such as those behind retrofit demand, and see the effect straight away.

The data refreshed every day (🔩 steel and aluminium prices, 💱 exchange rates, ⚡ solar generation) won't sit only in a separate real-time view: it will be **built into the rest of the analyses**, so the user can see how a change in these variables affects tracker costs, prices, market size and the model as a whole. How this content is split into screens will be defined as the project develops.

### 💡 Example uses

A commercial director could:

- 📍 pick a region and see how much utility-scale solar is being built, what share uses trackers and how much extra demand could come from retrofits
- 💰 check why a tracker plant costs more in one region than in another
- 🔩 follow how a rise in steel or freight prices feeds into tracker costs
- 📈 compare where each region's tracker market has been and where it is heading

---

## ⚙️ Technical vision

### 📡 Data sources

These are the sources explored so far; more sources and variables are likely to be added as the project develops.

**⚡ Daily, downloaded automatically (no API key needed)**

| Source | Data |
|---|---|
| 🏦 European Central Bank | Euro reference rates vs US dollar, Brazilian real, Indian rupee and Chilean peso |
| 📈 Yahoo Finance (`yfinance`) | US hot-rolled steel and aluminium futures; listed solar and tracker equities |
| 🔌 Red Eléctrica (REData API) | Daily solar PV generation and installed capacity in Spain |

**🗓️ Monthly or yearly, loaded when new figures come out**

| Source | Data |
|---|---|
| 🌍 IRENA, Ember | Installed capacity by country |
| 🇺🇸 US Energy Information Administration | New utility-scale plants |
| 💲 IRENA cost reports, NREL, Berkeley Lab | System costs, including tracker vs fixed-tilt plants |
| 📰 Industry press | Freight indices and module prices |
| 📁 Internal market model (Excel) | Attach rates, fixed-tilt installed base, segment split (replaceable by upload) |

### 🔁 Pipeline

- 🐍 A Python pipeline downloads the data, cleans it, aligns it by country, segment and date, and computes the derived metrics: tracker market size in GW and in value, new build vs retrofit, year-on-year growth and regional price indices.
- 🔗 **The daily series are linked to the model:** a change in steel prices or exchange rates feeds through to tracker cost and price estimates, and from there to the value of the market.
- 🗄️ Everything is stored in a single table of observations (source, series, date, value) plus a log of every update. The initial plan is **SQLite** locally and **PostgreSQL on AWS RDS** in production; switching only means changing one connection setting.
- ♻️ The first run downloads three years of history. After that, each daily run downloads the last two weeks and replaces those dates, so revisions are picked up and re-runs are safe.
- 🛡️ If one source fails, the others still update and the error is recorded and shown in the application.

### 🔮 Forecasting

PV additions, attach rates and prices will be estimated by region for the coming years. Because the series are annual and fairly short, a **single model will be trained on all countries together**, using past values and variables such as module prices or recent growth.

- 📐 Options to test: a regularised linear regression and a tree-based model
- 📏 Benchmark: a very simple baseline that extends the trend of recent years, to check whether the models actually improve on it
- 👀 Forecasts will be shown next to the historical data, but clearly separated from it

### 🖥️ Application and deployment

The application is built with **Dash and Plotly** 📊. The region and segment filters and the assumption controls update the results without reloading the page.

In the current version, the daily update runs in two places:

- 🤖 a scheduled **GitHub Actions** job every morning, which also runs the **pytest** test suite before downloading
- ⏰ a scheduler inside the application (**APScheduler**) that updates the data at 06:00 Madrid time and catches up on start-up if the last update is more than 20 hours old

The application will be deployed on **AWS EC2** ☁️, with the database on **AWS RDS**.

### 🧰 Tech stack

| Layer | Tools |
|---|---|
| 📥 Data acquisition | Python, requests, yfinance, pandas, openpyxl |
| ⏰ Scheduling | GitHub Actions, APScheduler |
| 🗄️ Storage | SQLAlchemy, SQLite (local) / PostgreSQL on AWS RDS |
| 🔮 Forecasting | scikit-learn |
| 📊 Visualisation | Dash, Plotly |
| ✅ Testing | pytest |
| ☁️ Deployment | AWS EC2, AWS RDS |

---

## ⚠️ Disclaimer

Course project. The company that inspired it is not named, and the market model figures shown are illustrative, not project data.

---

<div align="center">

Made by **Alejandra Botín Lehm**

🔆 🌍 ⚡ 🏭 🔋

</div>
