# 🚍 FlixBus Pricing Flagging System

## 📌 Overview

This project automates the detection of pricing inconsistencies in FlixBus listings by comparing each FlixBus service with similar buses and flagging cases where pricing deviates significantly.

The system is designed as a **fully automated Python pipeline** that:

* Identifies comparable buses
* Computes reference pricing
* Flags overpricing and underpricing
* Generates a structured Excel report

---

## ⚙️ How It Works

### 🔹 1. Input Data

* The system takes a **bus dataset (Excel/CSV)** as input.
* Due to file size constraints, the dataset is **not included in this repository**.

📂 **Dataset & Output Link (Google Drive):**
👉 https://docs.google.com/spreadsheets/d/1ykuIeBEEwjaV3h27HTrtoV6Dm09ZAIID/edit?usp=sharing&ouid=116510880194304700456&rtpof=true&sd=true

👉 Place the dataset file in the same folder as the script before running.

---

### 🔹 2. Similar Bus Identification

For each FlixBus service, comparable buses are selected based on:

* Same **Route Number**
* Same **Date of Journey (DOJ)**
* **AC Sleeper buses only**
* Departure time within **±2 hours window**
* Minimum number of reviews (data reliability)

👉 Handles **midnight edge cases** (e.g., 23:00 vs 01:00)

---

### 🔹 3. Pricing Logic

* Reference price = **Median of comparable buses**
* Adjustments applied:

  * Daytime discount (lower pricing expectation)
  * Seater/Sleeper configuration adjustment

---

### 🔹 4. Flagging Conditions

* 🔴 **TOO HIGH** → Price > +15% above comparable median
* 🔵 **TOO LOW** → Price < -15% below comparable median
* 🟢 **OK** → Within acceptable range
* ⚠️ **SKIP** → Insufficient data

---

### 🔹 5. Output

The system generates:

📊 **Flixbus_Pricing_Flagging_Output.xlsx**

Includes:

* Comparable buses used
* Price statistics (median, mean, quartiles)
* Price difference
* Flag indicator
* Adjustment details

---

## 🛠 Tech Stack

* Python
* Pandas
* NumPy
* OpenPyXL

---

## ▶️ How to Run

### 1. Install dependencies

```bash
pip install pandas numpy openpyxl
```

### 2. Add dataset

* Place input file (CSV/Excel) in project folder

### 3. Run script

```bash
python flixbus_pricing_automation.py bus_data.csv
```

### 4. Output generated

* Excel report with flagged pricing cases

---

## 🔄 Automation Plan (MVP)

This system can be automated as:

1. Daily dataset ingestion
2. Run Python script (batch job / cron)
3. Generate Excel report
4. Send alerts / integrate with dashboard

---

## ⚠️ Notes

* Dataset is large → shared via Google Drive instead of GitHub
* Both **input dataset and output file** are included in Drive link
* Designed for scalability and real-world pricing systems

---

## 🤖 AI Usage

AI tools (ChatGPT) were used for:

* Structuring logic
* Debugging implementation
* Designing automation workflow

---

## ✅ Conclusion

This solution provides a scalable and automated approach to detect pricing inefficiencies and can be extended into a real-time pricing intelligence system.
