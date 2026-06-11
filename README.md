# Agriculture Commodities, Prices & Seasons Analysis
## SocialCops Data Science Intern Challenge

## 📌 Project Overview
This project focuses on building data-driven insight packs to measure key trends in the agricultural sector of Maharashtra, India[cite: 1]. Using Agricultural Produce Market Committee (APMC) mandi price and quantity arrival data alongside government-mandated Minimum Support Prices (MSPs), this analysis aims to understand historical market behaviors, evaluate price fluctuations, and isolate seasonal effects across various commodities and APMCs[cite: 1].

---

## 📊 Dataset Description
The analysis utilizes two core datasets located in the `Mandi_Data/` directory:
1. **`CMO_MSP_Mandi.csv`**: Contains the Year, Commodity, Crop Type, and the Minimum Support Price (MSP) set by the Government.
2. **`Monthly_data_cmo.csv`**: Contains APMC-wise monthly market arrivals along with the minimum, maximum, and modal (average) prices per quintal for each commodity.

---

## 🛠️ Project Structure & Methodology

The analysis is broken down into four core structural sections:

### 1. Exploratory Data Analysis & Data Cleaning
* **Missing Value Imputation**: Identified missing values in the MSP dataset and executed a robust cleanup by forcing unreadable strings into a numeric schema for processing.
* **Time-Series Parsing**: Standardized the data structures by converting temporal attributes into explicit Pandas Datetime indices (`%Y` for MSP data and `%Y-%m` for monthly market data).

### 2. Outlier Detection & Handling
* Leveraged the **Interquartile Range (IQR) Method** to mathematically define and isolate anomalies within commodity pricing groups.
* Utilized Seaborn box plots to visually track price spreads across target timelines (2014–2016), highlighting major deviations (such as the March 2016 Bajri price anomaly).

### 3. Seasonality Detection & De-seasonalization
To ensure scalability, a generic framework was constructed and tested against a subset of clusters, including **Ahmednagar, Rahata, and Jamkhed** for primary commodities like **Bajri, Onion, and Capsicum**.
* **Stationarity Testing**: Applied the **Augmented Dickey-Fuller (ADF) Test** to establish whether time-series trends were stationary or required transformation.
* **Seasonality Profiling**: Identified both **Multiplicative** (e.g., Bajri in Ahmednagar/Rahata) and **Additive** (e.g., Bajri in Jamkhed) environments.
* **De-seasonalization**: Cleared out seasonal variances using **Log Transformations** (to convert multiplicative characteristics to additive) followed by **First-Order Differencing (Lag-1)** and **Seasonal-Trend Decomposition (STL)**.

### 4. MSP Comparison & Annual Price Fluctuations
* Compared actual market-driven APMC prices directly against the government's base MSP.
* Quantified maximum annual price fluctuations by mapping the spread between monthly high and low thresholds across distinct years:
  * **2014**: Highest variations occurred in **APMC: Rahata** and **Commodity: Capsicum**.
  * **2015**: Highest variations shifted to **APMC: Ahmednagar** and **Commodity: Onion** (driven by major nationwide crop supply deficits).
  * **2016**: Highest variations settled in **APMC: Ahmednagar** and **Commodity: Capsicum**.

---

## 📈 Key Insights & Takeaways
* **The MSP Gap**: For multiple core commodities (like Bajri), the minimum prices set by the government sat significantly lower than actual trading values inside the APMCs. 
* **Supply Shock & Market Vulnerability**: Price anomalies—like the massive Onion price surge in September 2015—were heavily tied to underlying supply drops and production deficits rather than normal seasonal rhythms.
* **Logistical Impacts**: A notable portion of localized price variance, especially when comparing volatile trading zones to stable baseline MSPs, is linked to varying transportation costs and the geographic distance between farming sectors and primary market hubs.

---

## 💻 Tech Stack Used
* **Language**: Python
* **Libraries**: Pandas, NumPy, Matplotlib, Seaborn, Statsmodels

---
*Analysis completed as part of the data science assignment framework.*[cite: 1]
