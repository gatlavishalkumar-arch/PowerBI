# ⏱️ Time Intelligence Functions in Power BI — DAX Project

A comprehensive **Power BI project** demonstrating real-world usage of
**Time Intelligence Functions** using **DAX** for business analytics
and financial reporting.

> 📺 Built as part of Power BI DAX learning series

---

## 🔗 Live Dashboard

| Resource | Link |
|----------|------|
| 🔗 **Live Report** | [Click here to view on Power BI](<iframe title="Bike data_Measure" width="600" height="373.5" src="https://app.powerbi.com/view?r=eyJrIjoiMTFjNWRmYjMtZWVhZC00ZmNhLWE4ZjQtYzQxOGVjMjZlODVjIiwidCI6Ijg4Zjk0NGQwLTEyNzgtNDVmOS04OGQ4LWRjODFiNWY3N2IxNyJ9" frameborder="0" allowFullScreen="true"></iframe>) |

---

## 📌 Project Overview

This project demonstrates how **DAX Time Intelligence Functions**
are used to analyze data across different time periods — comparing
current vs previous periods, calculating running totals, and
building year-over-year growth metrics.

---

## 🖼️ Dashboard Screenshot
<img width="1920" height="1023" alt="Between_dates" src="https://github.com/user-attachments/assets/520951d0-e1e8-4667-91b1-c7feee59b16f" />
<img width="1918" height="1027" alt="Last_30Days" src="https://github.com/user-attachments/assets/78d3932e-37f2-4761-8d12-cfa7f12f4d08" />
<img width="1915" height="1030" alt="Last_3Months" src="https://github.com/user-attachments/assets/04a7231a-8af2-4d24-ad9f-935ad572fb84" />
<img width="1916" height="1026" alt="All_Function" src="https://github.com/user-attachments/assets/a2ed050a-0a29-4c3b-9d16-54548c189f89" />
<img width="1912" height="1025" alt="ALLEXCEPT_function" src="https://github.com/user-attachments/assets/c9e3f8d4-f7f6-407a-a960-721eb8e9e026" />
<img width="1917" height="1027" alt="ALLSELECTED_Function" src="https://github.com/user-attachments/assets/738ec5c4-c137-4770-8328-d6a251c725de" />
<img width="1917" height="1030" alt="Previous_Quarter" src="https://github.com/user-attachments/assets/83981550-f84f-46ee-a705-f679ae19f3e9" />
<img width="1920" height="1027" alt="Previous_year" src="https://github.com/user-attachments/assets/95e36b24-a34d-49e4-b81b-8cecfae4809b" />
<img width="1918" height="1030" alt="Previous_month" src="https://github.com/user-attachments/assets/00dc8e77-fafa-4730-9e3d-107d0b5a7bef" />
<img width="1913" height="1027" alt="DateMTD" src="https://github.com/user-attachments/assets/c45eecad-3451-44f6-af98-837edd24dcab" />
<img width="1920" height="1031" alt="DatesQTD" src="https://github.com/user-attachments/assets/0386f577-b4a0-4977-a672-008d9500daeb" />
<img width="1920" height="1028" alt="DatesYTD" src="https://github.com/user-attachments/assets/80beb830-1c66-419d-94a9-18dec5d07eaf" />
<img width="1920" height="1027" alt="DateAdd" src="https://github.com/user-attachments/assets/427927ae-d39b-4884-930b-3156881dc0cd" />
<img width="1917" height="1030" alt="SUMMARIZE" src="https://github.com/user-attachments/assets/1815a430-bbec-439d-96a7-1abb5099155b" />
<img width="1917" height="1027" alt="Previous_Day" src="https://github.com/user-attachments/assets/408bd83b-8f3a-48e8-b84f-431f461797af" />
---

## ⏱️ Time Intelligence Functions Covered

### 1️⃣ TOTALYTD — Year to Date
```dax
Total Sales YTD = 
TOTALYTD(
    SUM(Sales[Amount]),
    'Date'[Date]
)
```
> Calculates cumulative sales from start of year to current date.

---

### 2️⃣ TOTALQTD — Quarter to Date
```dax
Total Sales QTD = 
TOTALQTD(
    SUM(Sales[Amount]),
    'Date'[Date]
)
```
> Calculates cumulative sales from start of quarter to current date.

---

### 3️⃣ TOTALMTD — Month to Date
```dax
Total Sales MTD = 
TOTALMTD(
    SUM(Sales[Amount]),
    'Date'[Date]
)
```
> Calculates cumulative sales from start of month to current date.

---

### 4️⃣ SAMEPERIODLASTYEAR — Previous Year
```dax
Sales Last Year = 
CALCULATE(
    SUM(Sales[Amount]),
    SAMEPERIODLASTYEAR('Date'[Date])
)
```
> Returns sales value for same period in previous year.

---

### 5️⃣ PREVIOUSMONTH — Previous Month
```dax
Sales Previous Month = 
CALCULATE(
    SUM(Sales[Amount]),
    PREVIOUSMONTH('Date'[Date])
)
```
> Returns sales value for previous month.

---

### 6️⃣ PREVIOUSQUARTER — Previous Quarter
```dax
Sales Previous Quarter = 
CALCULATE(
    SUM(Sales[Amount]),
    PREVIOUSQUARTER('Date'[Date])
)
```
> Returns sales value for previous quarter.

---

### 7️⃣ PREVIOUSYEAR — Previous Year Total
```dax
Sales Previous Year = 
CALCULATE(
    SUM(Sales[Amount]),
    PREVIOUSYEAR('Date'[Date])
)
```
> Returns total sales for entire previous year.

---

### 8️⃣ DATEADD — Custom Period Shift
```dax
Sales Last 3 Months = 
CALCULATE(
    SUM(Sales[Amount]),
    DATEADD('Date'[Date], -3, MONTH)
)
```
> Shifts date by specified interval — months, quarters, years.

---

### 9️⃣ YOY Growth % — Year over Year
```dax
YOY Growth % = 
DIVIDE(
    SUM(Sales[Amount]) - 
    CALCULATE(SUM(Sales[Amount]),
    SAMEPERIODLASTYEAR('Date'[Date])),
    CALCULATE(SUM(Sales[Amount]),
    SAMEPERIODLASTYEAR('Date'[Date]))
) * 100
```
> Calculates percentage growth compared to same period last year.

---

### 🔟 MOM Growth % — Month over Month
```dax
MOM Growth % = 
DIVIDE(
    SUM(Sales[Amount]) -
    CALCULATE(SUM(Sales[Amount]),
    PREVIOUSMONTH('Date'[Date])),
    CALCULATE(SUM(Sales[Amount]),
    PREVIOUSMONTH('Date'[Date]))
) * 100
```
> Calculates percentage growth compared to previous month.

---

## 📊 Functions Summary Table

| Function | Purpose | Period |
|----------|---------|--------|
| `TOTALYTD` | Cumulative total | Year to Date |
| `TOTALQTD` | Cumulative total | Quarter to Date |
| `TOTALMTD` | Cumulative total | Month to Date |
| `SAMEPERIODLASTYEAR` | Same period comparison | Last Year |
| `PREVIOUSMONTH` | Previous period | Last Month |
| `PREVIOUSQUARTER` | Previous period | Last Quarter |
| `PREVIOUSYEAR` | Previous period | Last Year |
| `DATEADD` | Custom date shift | Flexible |
| `YOY Growth %` | Growth calculation | Year over Year |
| `MOM Growth %` | Growth calculation | Month over Month |

---

## ⚠️ Prerequisites for Time Intelligence
---

## 🏗️ Data Model
---

## 📋 What This Demonstrates

- ✅ **YTD, QTD, MTD** calculations
- ✅ **Year-over-Year** & **Month-over-Month** growth
- ✅ **Previous period** comparisons
- ✅ **DATEADD** for flexible period shifting
- ✅ **Date table** setup & configuration
- ✅ Real-world **financial reporting** patterns
- ✅ **DAX best practices** for time calculations

---

## 🛠️ Tech Stack

- **Power BI Desktop** — Report development
- **DAX** — Time intelligence calculations
- **Power Query** — Data transformation
- **Data Modeling** — Star schema design
- **Date Table** — Time intelligence foundation

---

## 📁 Repository Structure
---

## 💡 Key Learnings

| Concept | Key Point |
|---------|-----------|
| Date Table | Must be continuous & marked |
| TOTALYTD | Resets every year automatically |
| SAMEPERIODLASTYEAR | Needs proper date relationship |
| DATEADD | Most flexible time shift function |
| YOY % | Use DIVIDE to avoid divide by zero |

---

## 👨‍💻 Author

**Vishal Kumar Gatla**
Senior Power BI Developer | DAX | Time Intelligence | Azure

[![LinkedIn](https://www.linkedin.com/in/vishalkumar-gatla-281915115/)
---

## 🏷️ GitHub Tags
