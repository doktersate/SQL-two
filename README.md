SQL-two
=======

1)	How many orders did each customer make? Use the items_ordered table. Select the customerid, number of orders they made, and the sum of their orders.
  select customerid, count(customerid), sum(price) from items_ordered group by customerid;
  
2)	How many orders did each customer make? Use the items_ordered table. Select the customerid, number of orders they made, and the sum of their orders if they purchased more than 1 item.
  select customerid, count(customerid), sum(price) from items_ordered group by customerid having sum(quantity)>1;
  
3)	Write a query using a join to determine which items were ordered by each of the customers in the customers table. Select the customerid, firstname, lastname, order_date, item, and price for everything each customer purchased in the items_ordered table.
  select customers.customerid, customers.firstname, customers.lastname, items_ordered.order_date, items_ordered.item,   items_ordered.price from customers, items_ordered where customers.customerid = items_ordered.customerid group by   customers.customerid;
  select customers.customerid, customers.firstname, customers.lastname, items_ordered.order_date, items_ordered.item, items_ordered.price from customers inner join items_ordered on customers.customerid = items_ordered.customerid where customers.customerid = items_ordered.customerid;
  
4) SELECT min(abs(price-100)),item FROM items_ordered;

5) Select all item that had prices between $50 and $100. Only use items that have both a c and an e in them. 
  select item from items_ordered where item like '%a%' and item like '%c%' and item like '%e%' having price between 50 and 100;
  
6) For all of the tents that were ordered in the items_ordered table, what is the price of the lowest tent?
  select min(price) from items_ordered where item like 'Tent'
  
7) Write a query to determine which customer purchased the most expensive item, excluding any items that cost over $1000. 
  select max(price), firstname, lastname from items_ordered inner join customers on customers.customerid = items_ordered.customerid where price<1000;
