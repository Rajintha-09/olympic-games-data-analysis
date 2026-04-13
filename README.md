# Olympic Games Data Analysis Dashboard

A comprehensive Power BI dashboard analyzing **Summer & Winter Olympic Games** medal performance, participation trends, and success metrics across all nations — spanning the full history of the Olympics.

---

## Dashboard Pages

| Page | Description |
|------|-------------|
| Overview | KPI cards, medal totals, participation summary |
| Summer Olympics Analysis | Participation vs medals, gold/silver/bronze breakdown |
| Winter Olympics Analysis | Participation vs medals, medal type comparison |
| Medal Distribution by Country | 100% stacked area chart across top nations |
| Season Comparison | Summer vs Winter medal totals by country |

---

## Dataset Used

| Dataset | Source | Coverage |
|---------|--------|----------|
| Olympic Games Medal Data (All Nations) | Wikipedia – All-time Olympic Games Medal Table | All-time |

**Columns included:**
- `Team (IOC code)` — Country name and IOC code
- `Number of games participated (SOG)` — Summer Olympics appearances
- `Gold / Silver / Bronze Medal (SOG)` — Summer medal counts
- `Total Medals (SOG)` — Total Summer medals
- `Number of games participated (WOG)` — Winter Olympics appearances
- `Gold / Silver / Bronze Medal (WOG)` — Winter medal counts
- `Total Medals (WOG)` — Total Winter medals
- `Combined Total (CT)` — All-time combined medal tally

---

## Tech Stack

- **Microsoft Excel (.xlsx)** — Data cleaning and preprocessing
- **Power BI Desktop** — Data modelling and DAX measures
- **DAX** — Custom KPI calculations and medal ratios

---

## Project Structure

```
Olympic-Games-Data-Analysis/
│
├── dataset/
│   └── olymics_gamess.csv                   # Cleaned dataset (Summer + Winter)
│
├── powerbi/
│   ├── Dashboard.pbix                        # Power BI dashboard file
│   └── dashboard.png                         # Dashboard screenshot
│
├── report/
│   ├── Olympic_Games_Data_Analysis.pdf       # Full analysis report (PDF)

└── README.md
```

---

## How to Run

1. Install **Power BI Desktop** — [Download here](https://powerbi.microsoft.com/desktop)
2. Clone or download this repository
3. Open `powerbi/Dashboard.pbix` in Power BI Desktop
4. If prompted, update the data source path to point to `dataset/olymics_gamess.csv` on your machine
5. Click **Refresh** to reload the data

---

## Data Model

The dataset uses a flat table structure with Summer (SOG) and Winter (WOG) columns stored side by side, enabling season filtering without unpivoting:

```
OlympicsTable
  ├── Team (IOC code)
  ├── SOG_Games, SOG_Gold, SOG_Silver, SOG_Bronze, SOG_Total
  └── WOG_Games, WOG_Gold, WOG_Silver, WOG_Bronze, WOG_Total
```

---

## DAX Measures

```dax
Total Medals (Combined) = SUM(OlympicsTable[Total Medals(CT)])

Summer Medal Rate (%) =
DIVIDE(
    SUM(OlympicsTable[Total Medals(SOG)]),
    SUM(OlympicsTable[Number of games participated(SOG)])
)

Winter Medal Rate (%) =
DIVIDE(
    SUM(OlympicsTable[Total Medals(WOG)]),
    SUM(OlympicsTable[Number of games participated(WOG)])
)

Gold Medal Share (Summer) =
DIVIDE(
    SUM(OlympicsTable[Gold Medal(SOG)]),
    SUM(OlympicsTable[Total Medals(SOG)])
)
```

---

## Key Findings

- **3,696** total games participated across all nations
- **22K+** total medals won (Summer + Winter combined)
- 🇺🇸 USA, 🇨🇳 China, and the former Soviet Union dominate **Summer** Olympics
- 🇳🇴 Norway and 🇩🇪 Germany lead the **Winter** Olympics medal tables
- Summer participation accounts for ~**87.87%** of all Olympic appearances
- Winter medal competition is more concentrated among a smaller group of nations

---

## Report

A full written analysis report is available in both PDF and Word format in the `/report` folder, covering:
- Data collection and preprocessing steps
- Dashboard development methodology
- Pattern analysis and key insights
- Conclusions and future work

---

## Reference

- Wikipedia: [All-time Olympic Games medal table](https://en.wikipedia.org/wiki/All-time_Olympic_Games_medal_table)

---
## Contributors
Chamali Abeysekara
Rajintha Hewanayaka
Hussein Ziyard
Nasir Mohomad

---
