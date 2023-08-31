				--- KPIs Requirement
					--- A. KPIs
                    
				--- Total Revenue 

select sum(total_price) as Revenue from pizza_sales;

				--- Average Order Value

select sum(total_price) / count(distinct order_id)  as Avg_Oder_Value from pizza_sales;

				--- Total Pizza Sold

select sum(quantity) as Pizza_Sold from pizza_sales;

				--- Total Order

select count(distinct order_id) as Total_Oder from pizza_sales; 
	
				--- Average Pizza Per Oder

select sum(quantity) / count(distinct order_id) as Avg_Pizza_Per_Oder from pizza_sales;

				--- Hourly Trend For Total Pizza Sold

select order_time as order_time from pizza_sales;

select datepart(hour, order_time) as order_hour, sum(quantity) as total_pizza_sold 
from pizza_sales
group by datepart(hour, order_time)
order by datepart(hour, order_time);

select * from pizza_sales;

				--- Weekly Trend For Total Orders

select * from pizza_sales;
				--- total_sales Pizza category by percantage

select pizza_category, sum(total_price) *100 / (select sum(total_price) from pizza_sales) as Percentage
from pizza_sales 
group by pizza_category;

select pizza_category, sum(total_price) as Price, (total_price) *100 / (select sum(total_price) from pizza_sales) as Percentage
from pizza_sales 
group by pizza_category;

select pizza_category, sum(total_price) as Price, (total_price) *100 / (select sum(total_price) from pizza_sales) as Percentage
from pizza_sales 
where month(order_date) = 1
group by pizza_category;

			--- Percentage of Sales by Pizza Size
            
select pizza_size, sum(total_price) as Price, sum(total_price) *100 / (select sum(total_price) from pizza_sales) as Percentage
from pizza_sales
group by pizza_size;

				--- Top 5 Best sales by Revenue
                
select pizza_name, sum(total_price) as Total_Revenue from pizza_sales
group by pizza_name
order by total_revenue desc
limit 5;

				--- Worst 5 Best sales by Revenue
                
select pizza_name, sum(total_price) as Total_Revenue from pizza_sales
group by pizza_name
order by total_revenue asc
limit 5;

				--- Top 5 Best sales by  Quantity

select pizza_name, sum(quantity) as total_quantity from pizza_sales
group by pizza_name
order by total_quantity desc
limit 5;

				--- Worst 5 Best sales by Quantity

select pizza_name, sum(quantity) as total_quantity from pizza_sales
group by pizza_name
order by total_quantity asc
limit 5;
				--- Top 5 Best sales by Order_Id

select pizza_name, count(distinct order_id) as total_orders from pizza_sales
group by pizza_name
order by total_orders desc
limit 5;
				--- Worst 5 Best sales by Order_Id
select pizza_name, count(distinct order_id) as total_orders from pizza_sales
group by pizza_name
order by total_orders asc
limit 5;










