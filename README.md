# SQL-project
The Pizza Sales project involves managing and analyzing data related to a pizza business.<br>
The database consists of four main tables:<br>

<b>Pizza</b>: Contains details about each type of pizza, including pizza ID,size,price and associated pizza type.<br>
<b>Pizza_Type</b>: Stores information about different pizza categories (e.g., vegetarian, non-vegetarian),ingrediants and name.<br>
<b>Orders</b>: Captures details of customer orders, such as order ID,date, and time.<br>
<b>Order_Details</b>: Represents the items in each order, including the order_detail_ID, pizza ID, quantity, and order_id.<br>

<b>Dataset used</b> = <a href = "https://github.com/Pavan-0156/SQL-project/blob/main/pizza_sales.zip"> PIZZA</a> 

# Questions solved
1.Retrieve the total number of orders placed.<br>
```sql
select count(order_id) as total_orders from orders
```
2.Calculate the total revenue generated from pizza sales.<br>
```sql
select
sum(order_details.quantity * pizzas.price) as revenue
from order_details join pizzas
on pizzas.pizza_id=order_details.pizza_id
```
3.Identify the highest-priced pizza.
```sql
select pizza_types.name, pizzas.price
from pizza_types join pizzas
on pizza_types.pizza_type_id = pizzas.pizza_type_id
order by pizzas.price desc limit 1;
```
4.Identify the most common pizza size ordered
```sql
select pizzas.size, count(order_details.order_details_id) as order_count
from pizzas join order_details
on pizzas.pizza_id = order_details.pizza_id
group by pizzas.size order by count(order_details.order_details_id) desc;
```
5.List the top 5 most ordered pizza types along with their quantities.
```sql
select pizza_type.name,sum(order_details.quantity)
from pizza_type join pizza
on pizza_type.pizza_type_id = pizza.pizza_type_id
join order_details
on order_details.pizza_id = pizza.pizza_id
group by pizza_types.name order by quantity desc limit 5;
```
