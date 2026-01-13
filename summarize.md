
# Summarize Two Table - unique combination

Below two are the input table:

Table1:
Country  |	City	|Transactions
----| ---- | ---
US|	Washington|	1
US	|New York|	2
Germany	|Berlin|	3
France|	Lyon|	4
US|	New York|	5
Germany	|Berlin|	6
France	|Lyon|	7

Table2:
Country|	City|	Transactions
-|--|--
US|	Houston	|A1
France|	Paris	|A2
France|	Paris	|A3
Togo	|Lome|	B1
France|	Paris|	B2
Togo	|Lome|	B3


Final Outcome should be in the below format:
all the unique Country - City Combination

Country	|City
-|-
US|	Houston
US|	Washigton
US	|New York
Germany	|Berlin
France|	Lyon
France|	Paris
Togo|	Lome


The DAX Query is = 
```
Combined = 
var table1 = SUMMARIZE(Sheet1, Sheet1[Country],Sheet1[City])
var table2 = SUMMARIZE(Sheet2, Sheet2[Country],Sheet2[City])
var final = UNION(table1,table2)
return final

```
