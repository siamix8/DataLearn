Установил postgre SQL Тут проблем не было 
Установил DBeaver аналогично проблем не было 
Загрузил данные в новую базу данных на postgres 
Покрутил простые селекты 
селекты по заданию


-- основные метрики (total_sales, total_profit, profit_ratio, profit_per_order, sales_per_customer)
select 	round(sum(o.sales),2) as total_sales ,
		round(sum(o.profit),2) as total_profit,
		round(sum(o.profit) / sum(o.sales) * 100,2) as profit_ratio,
		round(sum(o.sales) / count(distinct o.order_id),2)  as profit_per_order,
		round(sum(sales) / count(distinct customer_id), 2) as sales_per_customer ,
		round(avg(discount)* 100 ,2 ) as avg_discount_
from orders o 

 -- Moyntly sales per segment
select to_char(order_date::date, 'month, yyyy') as month, segment, round(sum(sales),2) sum_sales
from orders o
group by month, segment
order by 3 desc

--Sales by Product Category over time
select
segment,
sum(sales) as sales
from orders o
group by segment
order by segment ;

-- monthly sales be product category
select to_char(order_date::date, 'month, yyyy') as month, category , round(sum(sales),2) sum_sales
from orders o
group by month, category 
order by 3 desc


--Sales by Product Category over time
select
segment,
sum(sales) as sales
from orders o
group by segment
order by 1;


-- sales and profit by customer
select  distinct customer_name ,
		round(sum(sales),2 ) as total_sale_per_customer,
		sum(profit) as total_profit_per_customer
from orders o 
group by customer_name  
order by  total_sale_per_customer desc 

![2b05459efeb9d31943e1f0e365f05751](https://github.com/souluran/datalearn101/assets/102100090/156fde9e-dc6e-4c88-8bd6-dd68bafac967)
![3dd60d0de3fcd21895e9c7e96e5878b4](https://github.com/souluran/datalearn101/assets/102100090/bb63f686-be10-4db2-a451-b449c887cd83)
![7f83fadd8b90aaf6a12cba4b20e9e9f9](https://github.com/souluran/datalearn101/assets/102100090/78b8fbf1-2d81-483e-a7ea-e7a166a4ba66)
![c9b60d60b5e7ce1b8e7d02b84ad80d0c](https://github.com/souluran/datalearn101/assets/102100090/b5d9abca-01e6-45f4-ab97-f703a942055f)
![d3cf3087d88bac21c3f10dea7c5a0d72](https://github.com/souluran/datalearn101/assets/102100090/b2930be3-ccc9-425b-be4b-dd594026a8e7)
![d90046d69ceefaa06f4f7c14f258587c](https://github.com/souluran/datalearn101/assets/102100090/dce229c4-5a18-4a4f-b70a-e5742675b775)

