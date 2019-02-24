# Day 7 lab
## Goal
Use the `recipe` database to practice with INNER and OUTER joins.
## About the recipe database
* Each recipe in the database has information about itself, but there are also several other "lookup tables" that hold lists of abbreviations and categories for the various things about the recipe.
* A database schema that has this structure (lots of lookup tables) is sometimes called a *star schema*.
* The center of the star are the tables like *ingredients*, *recipes*, and *recipe_ingredients* that do all the work.
* The rest of the schema is made up of helper tables. We call these "lookup tables" because they are basically just lists of things where you can look things up. Lists of ingredients, the list of classes that a recipe can be in, the list of classes an ingredient can be in, the list of measurements that an ingredient can be measured in.
> Question to ponder: Why not just make these lookup tables into ENUM data types within the original table? In other words, why not just take the *recipe_classes* table and make it into an ENUM type inside the *recipes* table?

![recipes ERD](https://github.com/megansquire/CSC301Spr2019/blob/master/images/day7lab.1.png)

## Questions
1. Write the SQL to show each recipe class (Dessert, Hors D'Oeuvres, etc), and the count of recipes in that class. Do **not** show classes that have no recipes. Hint: you should see 6 rows returned.

2. Write the SQL to show every recipe that uses some kind of pepper. Show the recipe title and amount of pepper used. (We are interested in the SPICE 'pepper' not the vegetable 'green pepper', so make sure you only show the spices. Use the `ingredientClassDescription` to do this.) Also, write your query so that you DO NOT assume you know the `ingredientID` for any kind of 'pepper', and DO NOT assume you know the `ingredientClassID` for 'spice'. Hint: there will be about 8 recipes and 3 different kinds of pepper used in them.

3. Show each recipe class description, recipe id, and recipe title. Show the classes **even if** there are no recipes from that class. (Hint: Your results should demonstrate that there are no recipes in the Soup class.)

4. Show each recipe class and the count of recipes in that class. Show the class descriptions **even if** there are no recipes from that class. (Hint: You should have 7 records. Compare this approach to #1 above.)

5. Show each ingredient name and a count of how many times it was used in any recipe. For example, salt is used in 8 recipes. Show ingredients **even if** they were never used in a recipe. Sort the results in order of the count, from high to low.

6. One of your dinner guests is lactose-intolerant. Show the recipe titles and their recipe class for any recipe that is on the NO list for today  - make a list of recipes that have ingredients from the "Dairy", "Butter", or "Cheese" ingredient classes.

7. Write the SQL to find out the answer to: "if we added the total amount of pepper used in every recipe, how much pepper would we have used?" (Show the ingredients, total, and measurement method 'tsp','ounce' etc) DO NOT assume you know the ingredient ID for any kind of pepper.

8. Imagine you want to make every recipe in the Dessert class. Write the SQL to print the class description ("Dessert"), recipe title, and ingredient list, including ingredient name, the amount used in that recipe, and the way that ingredient is measured (measurement\_description). NOTE: you will have multiple lines for each recipe, but only 2 recipes overall.

9. Write the SQL to only find recipes in which there is no 'notes' field filled in. Show the Recipe Title, Recipe class description.

10. Write SQL to show the recipe class description, recipe name, ingredient names, ingredient step numbers, ingredient quantities and ingredient measurements for every recipe, sorted in class, title, and step number sequence.

11. List every ingredient by name, and a number indicating how many times this ingredient is used across all recipes. (Only show ingredients that are used at least once, and put them in order high to low and then in alpha order by ingredient name.)

> QUESTION FOR PONDERING: See how this query only returns 59 rows? Yet there are 79 ingredients listed in the ingredients table. So why does this query only return 59 of them? 

12. Show the measurement amount descriptions that are *never* used in the ingredients table. For example, measurement id 6 is "Pinch" which has never been used as an ingredient measurement amount. 
> Hint: use the [JOINs Venn diagram](https://github.com/megansquire/CSC301Spr2019/blob/master/Unit4/Unit4.1Notes.md) to find which query to use
