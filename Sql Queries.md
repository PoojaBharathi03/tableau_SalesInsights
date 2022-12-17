## 1.Data Preprocessing 

### Adding table total_sales_amount where sales amount is converted into inr

```
alter table sales.transactions
add total_sales_amount int;

update sales.transactions
set total_sales_amount = sales_amount*75;

```
### Deleting rows with null value
```
elete from sales.customers
where customer_code is null;

```

## 2.Data Analysis

### top customers by total sales
```
select custmer_name, total_sales_amount
from sales.customers cu
join sales.transactions tr
on cu.customer_code = tr.customer_code
group by custmer_name
order by total_sales_amount desc;
```

### sales quantity per market

```
select markets_name, sales_qty
from sales.transactions tr
join sales.markets mr
on tr.market_code = mr.markets_code
group by markets_name;
```

### top products by sales
```
select pr.product_code, tr.total_sales_amount 
from sales.products pr
join sales.transactions tr
on pr.product_code = tr.product_code
group by product_code
order by total_sales_amount desc;
```

### total sales per market
```
select markets_name, total_sales_amount
from sales.markets m 
join sales.transactions tr
on m.markets_code = tr.market_code
group by markets_name
order by total_sales_amount desc;
```
### zones having sales
```
select zone, total_sales_amount
from sales.markets m 
join sales.transactions tr
on m.markets_code = tr.market_code
group by zone
order by total_sales_amount desc;
```

### sales per year
```
select date, cy_date,year,month_name,date_yy_mmm,total_sales_amount
from sales.date dd
join sales.transactions tr
on dd.date = tr.order_date
```
