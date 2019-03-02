## Questions
1. Show wines (just the `wine_id` is fine) that have never been ordered.
```sql
SELECT w.wine_id
FROM wine w
LEFT OUTER JOIN wine_items wi
  ON w.wine_id = wi.wine_id
WHERE wi.wine_id IS NULL;
```
2.Write a query to show the customer id, first and last name, and the count of orders placed. (Count orders, not bottles, and not items).
```sql
SELECT wc.cust_id, wc.surname, wc.firstname, count(wo.order_id)
FROM wine_customer wc 
INNER JOIN wine_orders wo
  ON wo.cust_id = wc.cust_id
GROUP BY 1,2,3;
```
3. Write a query to display the wine id, wine name, winery name, wine year for all wines, then also show the cost from the inventory table and the average price per bottle when the wine was actually sold (items table).
```sql
SELECT w.wine_id ,w.wine_name, w.year, wr.winery_name, wi.cost, round(avg(wit.price/wit.qty),2) as 'Avg Price/bottle'
FROM wine w
INNER JOIN wine_inventory wi
  ON w.wine_id = wi.wine_id
INNER JOIN wine_items wit
  ON w.wine_id = wit.wine_id
INNER JOIN winery wr
  ON wr.winery_id = w.winery_id
GROUP BY 1,2,3,4,5;
```
4. Write a query to show the customer information (id and name), the count of orders placed (not bottles, not items), and the sum of all the money spent on these orders. NOTE that wine_items is joined to wine_orders by two columns (composite key). You must do an "INNER JOIN table2 ON column1=column1 AND column2=column2".
```sql
SELECT wc.cust_id, wc.surname, wc.firstname, COUNT(DISTINCT wi.order_id), SUM(wi.price * wi.qty)
FROM wine_customer wc
INNER JOIN wine_orders wo
  ON wo.cust_id = wc.cust_id
INNER JOIN wine_items wi
  ON wi.cust_id = wo.cust_id 
AND wi.order_id = wo.order_id
GROUP BY 1,2,3;
```
5. Write a query to list all the titles (Mr, Mrs, etc) and how many people have that title. Make sure to write the query so it will always list all titles, even if they have no one with the title.
```sql
SELECT title, count(*)
FROM wine_titles wt
LEFT OUTER JOIN wine_customer wc
  ON wt.title_id = wc.title_id
GROUP BY 1;
```
6. Some wines are blends, comprised of multiple types of grapes. The wine_variety table shows each wine and the grapes in it. The 'id' column indicates whether the grape is first, second, third, etc in the list. Write a query to show each wine id, name, type, year, and the number of varieties of grapes in that wine. Sort them high to low by number of grapes, and then alphabetically by the wine_name, type, and year.
```sql
SELECT wv.wine_id, w.wine_name, wt.wine_type, w.year, count( wv.id ) as 'count of grapes' 
FROM wine_variety wv
INNER JOIN wine w ON wv.wine_id = w.wine_id
INNER JOIN wine_type wt ON wt.wine_type_id = w.wine_type
GROUP BY 1 
ORDER BY 5 DESC, 2, 3, 4;
```
