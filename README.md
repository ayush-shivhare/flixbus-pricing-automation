# 🚍 FlixBus Pricing Flagging System

## 📌 Overview

This project identifies pricing inconsistencies in bus listings by comparing our buses with similar buses and flagging cases where the price deviates significantly.

The goal is to ensure competitive and optimal pricing using data-driven analysis.

---

## 🧠 Problem Statement

Given a dataset containing attributes like:

* Price
* Load (seat occupancy)
* Search ranking
* Departure time
* Ratings & reviews

We need to:

1. Identify **similar buses**
2. Compare prices with those buses
3. Flag cases where pricing is:

   * Too high
   * Too low

---

## ⚙️ Approach

### 🔹 1. Identifying Similar Buses

Buses are considered similar based on:

* **Route Number** → Ensures same journey
* **Departure Time Window** → Buses within a close time range (handles midnight wraparound)
* **AC / Non-AC Filter** → Ensures fair comparison

This ensures we only compare buses that a user would realistically consider as alternatives.

---

### 🔹 2. Price Comparison Logic

For each bus:

* Identify comparable buses
* Compute **average price of similar buses**
* Calculate **price difference**

#### 🚨 Flagging Conditions:

* 🔴 **Overpriced** → Our price significantly higher than average
* 🟢 **Underpriced** → Our price significantly lower than average

A threshold is used to avoid minor fluctuations.

---

## 📊 Output

The system generates an Excel file:

### Sheet 1 – Flagging Output

* Our Bus
* Comparable Buses
* Average Comparable Price
* Price Difference
* Flag Indicator (High / Low / Normal)

### Sheet 2 – Logic Explanation

* Explanation of similarity logic
* Explanation of flagging logic
* Assumptions made

---

## 🛠 Tech Stack

* Python
* Pandas
* NumPy
* Excel

---

## 🔄 Automation Plan (MVP)

The system can be automated as follows:

1. **Data Ingestion**

   * Daily dataset input (CSV/Excel)

2. **Processing Layer**

   * Python script to:

     * Identify similar buses
     * Compute price deviations
     * Generate flags

3. **Output Generation**

   * Automated Excel report

4. **Optional Enhancements**

   * Dashboard (Power BI / Tableau)
   * Alerts for pricing issues
   * Integration with pricing systems

---

## ⚠️ Assumptions

* Buses with same route and similar departure time are comparable
* AC and Non-AC buses are not directly compared
* Small price variations are ignored using a threshold

---

## 📂 Project Structure

```
flixbus-pricing-automation/
│── flixbus_pricing_automation.py
│── Flixbus_Pricing_Flagging_Output.xlsx
│── README.md
```

---

## 🤖 AI Usage

AI tools (ChatGPT) were used for:

* Structuring the solution
* Debugging code
* Designing automation workflow

---

## ✅ Conclusion

This system provides a scalable approach to detect pricing inefficiencies and can be extended into a real-time pricing intelligence tool.
