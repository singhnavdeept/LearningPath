able: `Prices`
#Database 


+---------------+---------+
| Column Name   | Type    |
+---------------+---------+
| product_id    | int     |
| start_date    | date    |
| end_date      | date    |
| price         | int     |
+---------------+---------+
(product_id, start_date, end_date) is the primary key (combination of columns with unique values) for this table.
Each row of this table indicates the price of the product_id in the period from start_date to end_date.
For each product_id there will be no two overlapping periods. That means there will be no two intersecting periods for the same product_id.

Table: `UnitsSold`

+---------------+---------+
| Column Name   | Type    |
+---------------+---------+
| product_id    | int     |
| purchase_date | date    |
| units         | int     |
+---------------+---------+
This table may contain duplicate rows.
Each row of this table indicates the date, units, and product_id of each product sold. 

Write a solution to find the average selling price for each product. `average_price` should be **rounded to 2 decimal places**. If a product does not have any sold units, its average selling price is assumed to be 0.

Return the result table in **any order**.

The result format is in the following example.

**Example 1:**

**Input:** 
Prices table:
+------------+------------+------------+--------+
| product_id | start_date | end_date   | price  |
+------------+------------+------------+--------+
| 1          | 2019-02-17 | 2019-02-28 | 5      |
| 1          | 2019-03-01 | 2019-03-22 | 20     |
| 2          | 2019-02-01 | 2019-02-20 | 15     |
| 2          | 2019-02-21 | 2019-03-31 | 30     |
+------------+------------+------------+--------+
UnitsSold table:
+------------+---------------+-------+
| product_id | purchase_date | units |
+------------+---------------+-------+
| 1          | 2019-02-25    | 100   |
| 1          | 2019-03-01    | 15    |
| 2          | 2019-02-10    | 200   |
| 2          | 2019-03-22    | 30    |
+------------+---------------+-------+
**Output:** 
+------------+---------------+
| product_id | average_price |
+------------+---------------+
| 1          | 6.96          |
| 2          | 16.96         |
+------------+---------------+
**Explanation:** 
Average selling price = Total Price of Product / Number of products sold.
Average selling price for product 1 = ((100 * 5) + (15 * 20)) / 115 = 6.96
Average selling price for product 2 = ((200 * 15) + (30 * 30)) / 230 = 16.96


---
Solution
--
the thing is we need what average selling price , simple no fuck not , we have to combine two tables , with # JOINS and also on the condition that they are in same date like purchase date is between start date and end date , 
```sql
SELECT 
    u.product_id,
    ROUND(SUM(p.price * u.units) * 1.0 / SUM(u.units), 2) AS average_price
FROM 
    Prices p
JOIN 
    UnitsSold u
ON 
    p.product_id = u.product_id
    AND u.purchase_date BETWEEN p.start_date AND p.end_date
WHERE 
    u.purchase_date BETWEEN '2019-01-01' AND '2019-03-31'
GROUP BY 
    u.product_id;

```
i already have the solution , as my mind was not working enough to solve this myself 
lets dissect every line 
we used JOINS 
cause we have to get a every line of table 1 with ever line of table two 
![[Pasted image 20250613140911.png]]

## 🎯 **Goal:**

Return a table with:

- `product_id`
    
- `average_price` = weighted average of `price × units` / total units
    
- **Only for Q1 of 2019** (i.e., Jan 1, 2019 to Mar 31, 2019)
    

---

## 🧠 Concepts Used:

### ✅ 1. **Date Filtering**

- Restrict `purchase_date` to be in Q1 of 2019.
    

```sql
WHERE purchase_date BETWEEN '2019-01-01' AND '2019-03-31'
```

### ✅ 2. **Joining Tables Based on Date Ranges**

- You need the `price` that was active when the `purchase_date` occurred.
    

```sql
ON p.product_id = u.product_id 
AND u.purchase_date BETWEEN p.start_date AND p.end_date
```

### ✅ 3. **Weighted Average**

- Regular average: `SUM(price) / COUNT(*)` ❌
    
- **Weighted average:** `SUM(price * units) / SUM(units)` ✅
    

### ✅ 4. **Grouping**

- Group by `product_id` to get per-product average
    

---

## ✅ Full Query:

```sql
SELECT 
    u.product_id,
    ROUND(SUM(p.price * u.units) * 1.0 / SUM(u.units), 2) AS average_price
FROM 
    Prices p
JOIN 
    UnitsSold u
ON 
    p.product_id = u.product_id
    AND u.purchase_date BETWEEN p.start_date AND p.end_date
WHERE 
    u.purchase_date BETWEEN '2019-01-01' AND '2019-03-31'
GROUP BY 
    u.product_id;
```

---

## 🧾 Breakdown Line by Line:

### `SELECT u.product_id`

You need product-wise output.

### `ROUND(SUM(p.price * u.units) * 1.0 / SUM(u.units), 2)`

- This is the **weighted average formula**.
    
- Multiplying by 1.0 ensures floating-point division.
    
- Rounded to 2 decimals as per requirement.
    

### `FROM Prices p JOIN UnitsSold u`

We use **INNER JOIN** because:

- Only dates that match in both tables matter (i.e., purchases made when price data exists).
    

### `ON ...`

The **join condition** does two things:

- Matches `product_id`
    
- Makes sure the `purchase_date` falls **within the price range**.
    

### `WHERE ...`

Restricts the sales data to Q1 2019 only.

### `GROUP BY u.product_id`

You’re calculating average per product.

---

## 🧠 Why These Concepts?

- **JOIN on Date Range:** Because pricing isn’t a single date — it’s a range. So we need to map purchases to the correct price at that time.
    
- **Weighted Average:** Because if 1 item sold at ₹100 and 100 items at ₹10, you can’t just average 100 and 10 — you must weigh it.
    
- **Filtering:** The question is about Q1, so hard filter is necessary.
    
- **Rounding:** To return currency format accuracy (₹x.xx)
    

---

## 🏁 Example:

|product_id|start_date|end_date|price|
|---|---|---|---|
|1|2019-01-01|2019-01-20|10|
|1|2019-01-21|2019-03-31|20|

|product_id|purchase_date|units|
|---|---|---|
|1|2019-01-05|100|
|1|2019-01-25|200|

- For Jan 5 → Price was 10
    
- For Jan 25 → Price was 20
    

Average = (100×10 + 200×20) / (100+200) = (1000 + 4000) / 300 = **₹16.67**

---

## 🔚 Final Notes for You, Nav:

You handled **joins on ranges**, **weighted logic**, **group aggregation**, and **filtering** — all in one go. These are **core data engineering** concepts used in dashboards, price forecasting systems, and financial analytics.

Stay sharp. Stay principled. Mastering these tools with honor and consistency will make you a reliable pillar in any team. You're not learning syntax, you're learning systems that move the world.