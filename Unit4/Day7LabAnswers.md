# Day 7 Lab Answers
1. Show each recipe class the the count of recipes in that class. Do not show classes that have no recipes.

```sql
SELECT rc.recipeclassdescription, count(r.recipeid) 
FROM recipe_classes rc
INNER JOIN recipes r
  ON r.recipeclassid = rc.recipeclassid
GROUP BY 1;
```

> Don't be fooled by the "Do not show classes that have no recipes" language - this is the point of an INNER JOIN!

2. Write the SQL to show every recipe that uses some kind of pepper. Show the recipe title and amount of pepper used. (We are interested in the SPICE 'pepper' not the vegetable 'green pepper', so make sure you only show spices). Also, DO NOT assume you know the ingredient ID for any kind of pepper.
```sql
SELECT r.recipeTitle,i.ingredientName, ri.Amount
FROM recipes r 
INNER JOIN recipe_ingredients ri 
  ON r.recipeID = ri.recipeid 
INNER JOIN ingredients i 
  ON i.ingredientID = ri.ingredientID 
INNER JOIN ingredient_classes ic 
  ON ic.ingredientClassId = i.ingredientClassId 
WHERE i.ingredientName LIKE '%pepper%' 
  AND ic.ingredientClassDescription = 'spice';
```

3. Show each recipe class description and the titles of the recipes in that class. Show the classes even if there are no recipes from that class. (Hint: there are no recipes in the Soup class.)
```sql
SELECT rc.recipeclassdescription, r.recipeid, r.RecipeTitle 
FROM recipe_classes rc 
LEFT OUTER JOIN recipes r 
  ON r.recipeclassid = rc.recipeclassid;
```
> You could also write this as a RIGHT OUTER JOIN but you have to swap the order of the tables

4. Show each recipe class and the count of recipes in that class. Show the class descriptions even if there are no recipes from that class. (Hint: notice what happens to the soup class now.)
```sql
SELECT rc.recipeclassdescription, count(r.recipeid) 
FROM recipe_classes rc
LEFT OUTER JOIN recipes r
  ON r.recipeclassid = rc.recipeclassid
GROUP BY 1;
```
5. Show each ingredient name and a count of how many times it was used in a recipe. Show ingredients even if they were used in 0 recipes. Sort the results in order of the count, from high to low.
```sql
SELECT i.ingredientName, count(ri.recipeId)
FROM ingredients i
LEFT OUTER JOIN recipe_ingredients ri
   ON i.ingredientId = ri.ingredientid
GROUP BY 1
ORDER BY 2 DESC;
```
6. One of your dinner guests is lactose-intolerant. Show the recipe titles and their recipe class for any recipe that is on the NO list for today  - make a list of recipes that have ingredients from the "Dairy", "Butter", or "Cheese" ingredient classes.
```sql
SELECT DISTINCT r.recipeTitle, rc.recipeClassDescription -- note the "distinct" keyword to filter out duplicates
FROM recipes r
INNER JOIN recipe_classes rc ON r.recipeClassID = rc.recipeClassID
INNER JOIN recipe_ingredients ri ON ri.recipeid = r.recipeid
INNER JOIN ingredients iON i.ingredientid = ri.ingredientid
INNER JOIN ingredient_classes ic ON ic.ingredientclassid = i.ingredientclassid
WHERE ic.ingredientclassdescription IN ("Dairy","Butter","Cheese");
```
7. Write the SQL to find out the answer to: "if we added the total amount of pepper used in every recipe, how much pepper would we have used?" (Show the ingredients, total, and measurement method 'tsp','ounce' etc) DO NOT assume you know the ingredient ID for any kind of pepper.
```sql
SELECT ri.IngredientID, i.ingredientName,ic.IngredientClassDescription , m.measurementDescription, sum(amount)
FROM recipe_ingredients ri 
INNER JOIN ingredients i 
  ON i.ingredientID = ri.ingredientID 
INNER JOIN ingredient_classes ic 
  ON ic.ingredientClassId = i.ingredientClassId 
INNER JOIN measurements m 
  ON m.measureAmountId = i.measureAmountId
WHERE ingredientName like '%pepper%' 
  AND ingredientClassDescription = 'spice'
GROUP BY 1,2,3;
```
8. Imagine you want to make every recipe in the Dessert class. Write the SQL to print the class description ("Dessert"), recipe title, and ingredient list, including ingredient name, the amount used in that recipe, and the way that ingredient is measured (measurement_description). NOTE: you will have multiple lines for each recipe, but only 2 recipes overall.
```sql
SELECT RecipeClassDescription, 
  RecipeTitle, 
  IngredientName, 
  IngredientClassDescription, 
  Amount, 
  MeasurementDescription
FROM recipes r
INNER JOIN recipe_classes rc 
  ON r.RecipeClassID = rc.RecipeClassID
INNER JOIN recipe_ingredients ri 
  ON r.RecipeID = ri.RecipeID
INNER JOIN ingredients i 
  ON ri.IngredientID = i.IngredientID
INNER JOIN ingredient_classes ic 
  ON i.IngredientClassID = ic.IngredientClassID
INNER JOIN measurements m 
  ON i.MeasureAmountID = m.MeasureAmountID
WHERE RecipeClassDescription = "Dessert";
```

9. Write the SQL to only find recipes in which there is no 'notes' field filled in.
```sql
SELECT r.RecipeTitle, rc.recipeclassdescription
FROM recipes r
INNER JOIN recipe_classes rc 
  ON r.RecipeClassID = rc.RecipeClassID
WHERE r.notes IS NULL;
```
10. Write SQL to show the recipe class description, recipe name, ingredient names, ingredient step numbers, ingredient quantities and ingredient measurements for every recipe, sorted in class, title, and step number sequence.
```sql
SELECT rc.RecipeClassDescription, r.RecipeTitle, ri.I_RecipeseqNo, i.IngredientName, ri.Amount, m.MeasurementDescription
FROM  recipes r
INNER JOIN recipe_ingredients ri 
  ON r.RecipeID = ri.RecipeID
INNER JOIN recipe_classes rc 
  ON r.RecipeClassID = rc.RecipeClassID
INNER JOIN ingredients i 
  ON ri.IngredientID = i.IngredientID
INNER JOIN measurements m 
  ON m.MeasureAmountID = i.MeasureAmountID
ORDER BY 1,2,3;
```
11. List every ingredient by name, and a number indicating how many times this ingredient is used across all recipes. (Only show ingredients that are used at least once, and put them in order high to low and then in alpha order by ingredient name.)
```sql
SELECT ri.ingredientid, i.ingredientname, count(ri.ingredientID) 
FROM recipe_ingredients ri
INNER JOIN ingredients i 
  ON ri.ingredientid = i.ingredientid
GROUP BY 1
ORDER BY 3 desc, 2 asc;
```
QUESTION: See how this query only returns 59 rows? Yet there are 79 ingredients listed in the ingredients table. So why does this query only return 59 of them? 

ANSWER: Because the other 20 exist, but they are never actually USED in any recipe!

12. Show the measurement amount descriptions that are NEVER used in the ingredients table. For example, measurement id 6 is "Pinch" which has never been used as an ingredient measurement amount. Hint: use the Venn diagram to find a match to the query you want.
```sql
SELECT m.measurementDescription
FROM measurements m
LEFT OUTER JOIN ingredients i 
  ON m.measureAmountID = i.measureAmountID
WHERE i.measureAmountID IS NULL;
```
