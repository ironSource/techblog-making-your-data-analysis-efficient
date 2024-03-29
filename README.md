## Making your data analysis efficient with the PinPointer dashboard
[Medium Post](https://www.google.com)
### Data source - PinPointer - User Impressions.csv:
We made a dataframe for you to play with. 

The dataframe has 4 columns:
* Date - timestamp, mm-dd-yyyy
* Product - String
* Country - country code, string, 2 letters
* Impressions - number of users impressions

Each row represent total impressions per a specific date, specific product in a specific cc.

Before you start to write your PinPointer you need to organize the data. Use this query as a start:
```sql
with country as(
select 'country' as indicator ,date,  cc as name, SUM(impressions) as impressions
from table
group by 1,2,3
order by 2,4 desc
)
, product as(
select 'product' as indicator,date, product as name, sum(impressions) as impressions
from table
group by 1,2,3
order by 2,4 desc
)
select *
from country
union all 
select *
from product
```
