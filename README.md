# 🏏 IPL Analytics Suite (2008-2024) - End-to-End Power BI Project

## 📌 Project Overview
"Gut feelings are expensive. Data is priceless."
In the IPL, franchise owners argue over match-ups based on intuition. I built this **IPL Strategic Analytics Suite** to transform **2.5 Lakh+ raw data points** into actionable intelligence for Captains and Coaches.

This dashboard doesn't just display stats; it answers strategic questions like:
* "Does winning the toss guarantee a win at Wankhede?"
* "Who is the true 'Death Over' specialist?"
* "Which bowler is Virat Kohli's statistical weakness?"

## 🛠️ Tech Stack
* **Tool:** Power BI Desktop
* **Language:** DAX (Data Analysis Expressions)
* **ETL:** Power Query (Data cleaning & Transformation)
* **Data Source:** Kaggle (IPL Dataset 2008-2024)

## 🔍 Key Features & Insights
### 1. **App-Like Navigation (UI/UX)**
Instead of standard tabs, I built a central **Home Page** with navigation buttons, creating a seamless mobile-app experience.

### 2. **Advanced DAX Logic (True Win %)**
**Problem:** Raw data lists matches with 'Team 1' and 'Team 2'. A standard relationship only filters one column, calculating incorrect win percentages.
**Solution:** I used DAX variables to manually count matches where a team was *either* Home *or* Away.
```dax
True Win % = 
VAR CurrentTeam = SELECTEDVALUE('Teams'[Team Name])
VAR MatchesPlayed = CALCULATE(
    COUNTROWS('matches'), 
    'matches'[team1] = CurrentTeam || 'matches'[team2] = CurrentTeam
)
RETURN DIVIDE([Total Wins], MatchesPlayed, 0)
