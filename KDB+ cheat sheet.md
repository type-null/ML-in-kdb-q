Assuming your database is saved on the e: drive in a file name “dbName”
 
To start q using a disk swap file to extend physical memory (that’s two hyphens, not an em dash). To use the “e:” drive for swap space use “e:/” instead of “filename”

```q
q —m filename
```
Load a dbName from drive e:
```q
load `e:/dbName
```
Counting Rows
```q
count dbName
```
Assuming you have a table with the columns DATE, TICKER, and VALUE, get Unique Values
```q
select distinct VALUE from dbName
```
Using a date range
```q
select from dbName where DATE>2000.01.01, DATE<2010.01.01
```

For fields or tickers with embedded spaces, convert to symbol in the query
```q
select from dbName where TICKER=`$("SPX INDEX")
```
Select data excluding nulls
```q
y: select from dbName where not null VALUE
```
Remove underscores from TICKER
```q
bName: update `$ssr[;"_";" "] each string TICKER from dbName
```
Remove duplicates
```q
`dbName: distinct `dbName
save `dbName
```
Find the median frequency of a time series
```q
f: select med DATE-prev DATE by TICKER, FIELD from dbName
 
f: select med DATE-prev DATE by TICKER, FIELD from dbName where DATE>2019.01.01
```
To check the memory allocation
```q
\w
```
Dates since Dec 25
```q
f: select by TICKER, FIELD, DATE from ieorNum where DATE>2019.12.25
```
Sort by date
```q
dbName: `TICKER`FIELD`DATE xasc dbName
```
Delete table
```q
delete f from `.
```
Garbage clean up
```q
Q.gc[]
```
Detailed memory check
```q
Q.w[]
```
Save query “f”
```q
save `f.csv
```