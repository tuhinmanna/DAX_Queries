There is a table with id and Transaction Date .<br>

Our Goal is to create a new column with previous Transaction dates, (lag func in sql) <br>


<img width="308" height="186" alt="image" src="https://github.com/user-attachments/assets/af5fdf2f-3fd4-40ee-92d1-ca1ee24a2c86" /> <br>

Solution: <br>

Result = MINX(FILTER(Sheet1,Sheet1[ID] = EARLIER(Sheet1[ID])-1), Sheet1[Transaction_Date])
