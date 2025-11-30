

# ⚡ PRNG Survival Prediction Pipeline  
### _A complete end-to-end pipeline for collecting, analyzing, and predicting PRNG (0/1) sequences._





## 🚀 Overview  
Predicting PRNG binary sequences is **not a common challenge** — it involves real-time ingestion, data transformation, streak analysis, anomaly detection, and delivering actionable predictions.

This umbrella repository links together all **four core components** of the full pipeline:

1. **Hybrid Data Scraper**  
2. **PRNG Data Insights Dashboard**  
3. **Long Streak Alert System**  
4. **Telegram Live Prediction Bot**

This repo is your **single entry point** to understand the entire system: what each part does, how the flow works, and where everything is located.



## 🧠 Full Pipeline Architecture

<pre style="white-space: pre;">
┌──────────────────────────────────────────────────────────────┐
│                       PRNG DATA SOURCE                        │
└───────────────▲──────────────────────────────▲────────────────┘
                │                              │
                │ real-time rounds (numeric)   │
                │                              │
                ▼                              ▼
        ┌────────────────────────┐     ┌────────────────────────┐
        │   WebSocket Listener    │     │      API Fallback      │
        │ (live event ingestion)  │     │ (recovery & sync)      │
        └──────────────┬─────────┘     └──────────────┬─────────┘
                        │                              │
                        └──────────────┬───────────────┘
                                       ▼
                         ┌────────────────────────────┐
                         │         HYBRID SCRAPER     │
                         │   (merge, dedupe, validate)│
                         └──────────────┬─────────────┘
                                        │
                                        ▼
                         ┌────────────────────────────┐
                         │           MONGODB           │
                         │   raw events (numeric)      │
                         └──────────────┬─────────────┘
                                        │ extract + transform
                                        ▼
                         ┌────────────────────────────┐
                         │     DAY-WISE CSV BUILDER    │
                         │ numeric → small/big → 0/1   │
                         └──────────────┬─────────────┘
                                        │
             ┌──────────────────────────┼───────────────────────────┐
             │                          │                           │
             ▼                          ▼                           ▼
 ┌────────────────────────┐  ┌────────────────────────┐  ┌────────────────────────┐
 │   STREAMLIT DASHBOARD  │  │  STREAK ALERT SYSTEM   │  │ TELEGRAM PREDICTION BOT│
 │  data insights & plots │  │ detect 7/10/12+ streaks│  │ next-round predictions │
 └────────────────────────┘  └────────────────────────┘  └────────────────────────┘
</pre>


# 🔗 Component Repositories (with Demo Links)

### 1️⃣ **Hybrid PRNG Data Scraper**  
**Repo:** [prng-hybrid-data-scraper](https://github.com/parikshit-labs/prng-hybrid-data-scraper)  
**Sample Scraped Data:**  
[Sample CSV](https://github.com/parikshit-labs/prng-streamlit-dashboard/blob/main/attached_assets/sample_csv_1.csv)

**What it does:**  
- Hybrid WebSocket + API scraper  
- Stores raw numeric rounds in MongoDB  
- Extractor converts numeric → small/big → **binary (0/1)**  
- Produces **day-wise cleaned CSVs** used by the entire pipeline  



### 2️⃣ **PRNG Data Insights Dashboard (Streamlit)**  
**Repo:** [prng-streamlit-dashboard](https://github.com/parikshit-labs/prng-streamlit-dashboard)  
**Live Demo:**  
[Open Streamlit Dashboard](https://prng-app-dashboard-vgs2fwzvgxysnenlusyg88.streamlit.app/)

**What it does:**  
- Visualizes 0/1 PRNG data  
- Shows streak maps, distributions, daily trends  
- Contains sample processed CSV files  
- Publicly deployed for demonstration  



### 3️⃣ **Long Streak Alert System**  
**Repo:** [prng-streak-alert-system](https://github.com/parikshit-labs/prng-streak-alert-system)  
**Screenshots (Alert Examples):**  
[Alert Screenshots](https://github.com/parikshit-labs/prng-streak-alert-system/tree/main/screenshots)

**What it does:**  
- Scans processed CSVs  
- Detects **long streaks** (7+, 10+, 12+, etc.)  
- Generates alert messages (Telegram/console)  
- Production logic private — screenshots + demo logic provided  



### 4️⃣ **Telegram Live Prediction Bot**  
**Repo:** [prng-live-prediction-bot](https://github.com/parikshit-labs/prng-live-prediction-bot)  
**Screenshots (Bot Demo):**  
[Prediction Bot Screenshots](https://github.com/parikshit-labs/prng-live-prediction-bot/tree/main/screenshots)

**Bot Status:** Offline (private) — demo screenshots included  

**What it does:**  
- Sends next-round predictions using survival-based logic  
- Implements `/start`, subscription, auto-updates  
- Formats prediction messages as Telegram notifications  



## 📌 Quick “Where to Find What”

| Component | What It Contains | Link |
|----------|------------------|------|
| **Hybrid Scraper** | Real-time ingestion, MongoDB write, extractor, CSV builder | [prng-hybrid-data-scraper](https://github.com/parikshit-labs/prng-hybrid-data-scraper) |
| **Dashboard** | Streamlit UI, insights, charts, sample CSV | [prng-streamlit-dashboard](https://github.com/parikshit-labs/prng-streamlit-dashboard) |
| **Alert System** | Long streak detection + alert screenshots | [prng-streak-alert-system](https://github.com/parikshit-labs/prng-streak-alert-system) |
| **Prediction Bot** | Bot logic + sample outputs | [prng-live-prediction-bot](https://github.com/parikshit-labs/prng-live-prediction-bot) |



## 📝 Summary

This umbrella repo gives you:
- A **high-level understanding** of the entire PRNG pipeline  
- A **visual pipeline diagram**  
- Direct **links to all 4 repositories**  
- Live **Streamlit deployment**  
- Links to screenshots for alert + prediction modules  
- Sample scraped data (for reproducibility)  

Use this repo link in your **resume** under “Major Project” or “Portfolio”.



## 👤 Author  
**GitHub:** [parikshit-labs](https://github.com/parikshit-labs)


Built with ⚡ data, 📊 insights, and 🎯 survival-based prediction logic.


---

<div align="center">
Built with ⚡ data, 📊 insights, and 🎯 survival-based prediction logic.
</div>


