# Extra practice questions 

## ERD
![wine erd](https://github.com/megansquire/CSC301Spr2019/blob/master/images/wineERD.png)
## Questions
1. Write a query to show wines (displaying just the `wine_id` is fine) that have never been ordered.

2. Write a query to show the customer id, first and last name, and the count of orders placed. (Count orders, not bottles, and not items).

3. Write a query to display the wine id, wine name, winery name, wine year for all wines, then also show the cost from the `inventory` table and the average price per bottle when the wine was actually sold (`items` table).

4. Write a query to show the customer information (id and name), the count of orders placed (not bottles, not items), and the sum of all the money spent on these orders. NOTE that `wine_items` is joined to `wine_orders` by two columns (a "composite key"). You must do an "INNER JOIN table2 ON column1=column1 AND column2=column2".

5. Write a query to list all the customer titles (Mr, Mrs, etc) and how many people have that title. Make sure to write the query so it will always list all titles, even if they have no one with the title.

6. Some wines are blends, comprised of multiple types of grapes. The `wine_variety` table shows each wine and the grapes in it. The `id` column indicates whether the grape is first, second, third, etc in the list. Write a query to show each wine id, name, type, year, and the number of varieties of grapes in that wine. Sort them high to low by number of grapes, and then alphabetically by the `wine_name`, `type`, and `year`.
