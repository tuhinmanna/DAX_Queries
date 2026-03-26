# 🧠 Advanced DAX Interview Challenge

## ❓ Problem Statement

You are given a **Sales** table:

| CustomerID | OrderDate | Revenue |
|------------|----------|--------|
| A          | Jan      | 100    |
| A          | Feb      | 200    |
| A          | Mar      | 0      |
| B          | Jan      | 50     |
| B          | Mar      | 150    |
| C          | Feb      | 300    |

### 👉 Requirement

Create a DAX measure to calculate:

> **Retention Revenue** = Revenue generated from customers who made purchases in **both the current month AND the previous month**

---


- Requires understanding of **filter context vs row context**
- Needs **dynamic time shifting**
- Must handle **customer-level logic before aggregation**
- Avoids incorrect results due to **direct filtering on aggregated values**

---

## ✅ Solution

```DAX
Retention Revenue = 
VAR CurrentMonthCustomers =
    CALCULATETABLE(
        VALUES(Sales[CustomerID])
    )

VAR PreviousMonthCustomers =
    CALCULATETABLE(
        VALUES(Sales[CustomerID]),
        DATEADD('Date'[Date], -1, MONTH)
    )

VAR RetainedCustomers =
    INTERSECT(CurrentMonthCustomers, PreviousMonthCustomers)

RETURN
CALCULATE(
    SUM(Sales[Revenue]),
    KEEPFILTERS(RetainedCustomers)
)
