
# Calculating net sale with discount

Below two are the input table:

Table1:
Date|	Product ID|	Product Price|	Discount (%)
-|-|-|-
02-05-2026|	1	|100	|30%
05-05-2026|	2	|300	|20%
09-05-2026|	3	|250|	10%
12-05-2026|	4	|450|	15%
22-05-2026|	5	|50|	5%
26-05-2026|	6	|550|	25%


Final Outcome should be in the same format with one column added which will show the final price

>
If the value is present with % , we can open power query and add a new column from example. then divide all values by 100.



The DAX Query is = 
```
Final_price_measure = sumx(Sheet1, (1-Sheet1[Discount (%)])*Sheet1[Product Price])

```
If , Create a new column: 
```
Final_price_col = (1-Sheet1[Discount (%)]) * Sheet1[Product Price]
```
