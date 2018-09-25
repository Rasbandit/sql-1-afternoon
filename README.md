<img src="https://s3.amazonaws.com/devmountain/readme-logo.png" width="250" align="right">

# Project Summary

In this project we will be practicing inserting and querying data using SQL. We'll make use of an existing database called DVD rental that can be downloaded here <a href="http://www.postgresqltutorial.com/postgresql-sample-database/">Click me</a>

## Setup

- Once you have downloaded the `.zip` extract the file from it, and it should be a `.tar` file.
- Right click your local database and create a new database called dvd_rental.
- Then right click your new `dvd_rental` database and select restore.
- Make sure the format is `Custom or tar` then select the button on the right of Filename with the three dots `...` inside it.
- This will open a file explorer, you will need to navigate to where you extracted the `dvd_rental.tar` file.
    - Make sure you change the Format: to all files in the bottom right.
- Once you have found your file press select
- Then press restore.
- you should now have all the tables you need for todays afternoon project.

<details>
    <summary>Detailed Images</summary>
    <p align="center">
        <img src="/readme_assets/create-database.jpg">
    </p>
    <br/>
     <p align="center">
    <img src="/readme_assets/create-name.jpg">
    </p>
    <br/>
     <p align="center">
    <img src="/readme_assets/restore-1.jpg">
    </p>
    <br/>
     <p align="center">
    <img src="/readme_assets/restore-2.jpg">
    </p>
    <br/>
     <p align="center">
    <img src="/readme_assets/restore-3.jpg">
    </p>
</details>

<br/>
Use [www.sqlteaching.com](http://www.sqlteaching.com/) or [sqlbolt.com](http://sqlbolt.com/) as resources for the missing keywords you'll need.

## Table - people

### Instructions

1. Create a table called `person` that records a `person`'s `id`, `name`, `age`, `height` ( in cm ), `city`, `favorite_color`.
    * `id` should be a SERIAL PRIMARY KEY
2. Add 5 different people into the `person` table.
    * Remember to not include the `id` because it should auto-increment.
3. List all the people in the `person` table by `height` from tallest to shortest.
4. List all the people in the `person` table by `height` from shortest to tallest.
5. List all the people in the `person` table by `age` from oldest to youngest.
6. List all the people in the `person` table older than `age` 20.
7. List all the people in the `person` table that are exactly 18 years old.
8. List all the people in the `person` table that are less than 20 years old and older than 30.
9. List all the people in the `person` table that are not 27 (Use not equals).
10. List all the people in the `person` table where their `favorite_color` is not red.
11. List all the people in the `person` table where their `favorite_color` is not red and is not blue.
12. List all the people in the `person` table where their `favorite_color` is orange or green.
13. List all the people in the `person` table where their `favorite_color` is orange, green or blue (use IN).
14. List all the people in the `person` table where their `favorite_color` is yellow or purple (use IN).

### Solution

<details>

<summary> <code> SQL Solutions </code> </summary>

<details>

<summary> <code> #1 </code> </summary>

```sql
CREATE TABLE person ( ID SERIAL PRIMARY KEY, name string, age integer, height integer, city string, FavoriteColor string );
```

</details>

<details>

<summary> <code> #2 </code> </summary>

```sql
INSERT INTO person ( name, age, height, city, FavoriteColor ) VALUES ( "First Last", 21, 182, "city", "Color" );
```

</details>

<details>

<summary> <code> #3 </code> </summary>

```sql
SELECT * FROM person ORDER BY height DESC;
```

</details>

<details>

<summary> <code> #4 </code> </summary>

```sql
SELECT * FROM person ORDER BY height ASC;
```

</details>

<details>

<summary> <code> #5 </code> </summary>

```sql
SELECT * FROM person ORDER BY age DESC;
```

</details>

<details>

<summary> <code> #6 </code> </summary>

```sql
SELECT * FROM person WHERE age > 20;
```

</details>

<details>

<summary> <code> #7 </code> </summary>

```sql
SELECT * FROM person WHERE age = 18;
```

</details>

<details>

<summary> <code> #8 </code> </summary>

```sql
SELECT * FROM person WHERE age < 20 OR age > 30;
```

</details>

<details>

<summary> <code> #9 </code> </summary>

```sql
SELECT * FROM person WHERE age != 27;
```

</details>

<details>

<summary> <code> #10 </code> </summary>

```sql
SELECT * FROM person WHERE FavoriteColor != "red";
```

</details>

<details>

<summary> <code> #11 </code> </summary>

```sql
SELECT * FROM person WHERE FavoriteColor != "red" AND FavoriteColor != "blue";
```

</details>

<details>

<summary> <code> #12 </code> </summary>

```sql
SELECT * FROM person WHERE FavoriteColor = "orange" OR FavoriteColor = "green";
```

</details>

<details>

<summary> <code> #13 </code> </summary>

```sql
SELECT * FROM person WHERE FavoriteColor IN ( "orange", "green", "blue" );
```

</details>

<details>

<summary> <code> #14 </code> </summary>

```sql
SELECT * FROM person WHERE FavoriteColor IN ( "yellow", "purple" )
```

</details>

</details>

## Table - order

### Instructions

1. Create a table called `order` that records: `person_id`, `product_name`, `product_price`, `quantity`.
2. Add 5 Orders to the `order` table.
    * Make orders for at least two different people.
    * `person_id` should be different for different people.
3. Select all the records from the `order` table.
4. Calculate the total number of products ordered.
5. Calculate the total `order` price.
6. Calculate the total `order` price by a single `person_id`.

### Solution

<details>

<summary> <code> SQL Solutions </code> </summary>

<details>

<summary> <code> #1 </code> </summary>

```sql
CREATE TABLE order ( person_id integer, product_price string, product_price float, quantity integer );
```

</details>

<details>

<summary> <code> #2 </code> </summary>

```sql
INSERT INTO order ( person_id, product_price, product_price, quantity ) VALUES ( 0, "Product", 12.50, 2 );
```

</details>

<details>

<summary> <code> #3 </code> </summary>

```sql
SELECT * FROM order;
```

</details>

<details>

<summary> <code> #4 </code> </summary>

```sql
SELECT SUM(quantity) FROM order;
```

</details>

<details>

<summary> <code> #5 </code> </summary>

```sql
SELECT SUM(product_price * quantity) FROM order;
```

</details>

<details>

<summary> <code> #6 </code> </summary>

```sql
/* The value of person_id depends on what IDs you used. Use a valid ID from your table */
SELECT SUM(product_price * quantity) FROM order WHERE person_id = 0;
```

</details>

</details>

## Table - artist

### Instructions

1. Add 3 new Actors to the `actor` table. ( It's already created )
    - You can ignore the last_update column and not put anything in it.
2. Select 10 actors in reverse alphabetical order.
3. Select 5 actors in alphabetical order.
4. Select all actors whose `first name` start with "Al".
5. Select all artists whose `first name` contain the letters "th".

### Solution 

<details>

<summary> <code> SQL Solutions </code> </summary>

<details>

<summary> <code> #1 </code> </summary>

```sql
INSERT INTO actor ( first_name, last_name ) VALUES ( 'Bob', 'Ross' );
```

</details>

<details>

<summary> <code> #2 </code> </summary>

```sql
SELECT * FROM actor ORDER BY first_name Desc LIMIT 10;
```

</details>

<details>

<summary> <code> #3 </code> </summary>

```sql
SELECT * FROM actor ORDER BY first_name ASC LIMIT 5;
```

</details>

<details>

<summary> <code> #4 </code> </summary>

```sql
SELECT * FROM actor WHERE first_name LIKE 'Al%';
```

</details>

<details>

<summary> <code> #5 </code> </summary>

```sql
SELECT * FROM actor WHERE first_name LIKE '%th%';
```

</details>

</details>

## Table - film

### Instructions

1. List all films `title`, `description`, and `rating` that are rated pg-13.
2. Find the `length` of the shortest film.
3. Find the `length` of the longest film.
4. Find every `film_id` from the `film_category` table where the category is `comedy`
   * You will need to query the `category` table to find the id for Vomedy Movies
5. Count how many films are of type `comedy`.

### Solution

<details>

<summary> <code> SQL Solutions </code> </summary>

<details>

<summary> <code> #1 </code> </summary>

```sql
SELECT title, description, rating
FROM film
WHERE rating = 'PG-13'
```

</details>

<details>

<summary> <code> #2 </code> </summary>

```sql
SELECT MAX(length) FROM FILM;
```

</details>

<details>

<summary> <code> #3 </code> </summary>

```sql
SELECT MIN(length) FROM FILM;
```

</details>

<details>

<summary> <code> #4 </code> </summary>

```sql
SELECT * 
FROM film_category
WHERE category_id = 5
```

</details>

<details>

<summary> <code> #5 </code> </summary>

```sql
SELECT Count(*)
FROM film_category
WHERE category_id = 5
```

</details>

</details>

## Table - payment

### Instructions

1. Count how many rentals were made by `customer_id` 25.
2. Find the largest order total amount.
3. Find the smallest order total amount.
4. Find all orders bigger than $5.
5. Count how many orders were smaller than $5.
6. Count how many orders were made by customers 255, 341, and 124 (use IN).
7. Get the average total of the orders.
8. Get the total sum of the orders.

### Solution

<details>

<summary> <code> SQL Solutions </code> </summary>

<details>

<summary> <code> #1 </code> </summary>

```sql
SELECT COUNT(*) FROM payment
WHERE customer_id = 25;
```

</details>

<details>

<summary> <code> #2 </code> </summary>

```sql
SELECT MAX(amount) FROM payment;
```

</details>

<details>

<summary> <code> #3 </code> </summary>

```sql
SELECT MIN(amount) FROM payment;
```

</details>

<details>

<summary> <code> #4 </code> </summary>

```sql
SELECT *
FROM payment
WHERE amount > 5;
```

</details>

<details>

<summary> <code> #5 </code> </summary>

```sql
SELECT COUNT(*)
FROM payment
WHERE amount < 5;
```

</details>

<details>

<summary> <code> #6 </code> </summary>

```sql
SELECT COUNT(*)
FROM payment
WHERE customer_id in (255, 341, 124);
```

</details>

<details>

<summary> <code> #7 </code> </summary>

```sql
SELECT AVG(amount) FROM payment;
```

</details>

<details>

<summary> <code> #8 </code> </summary>

```sql
SELECT SUM(amount) FROM payment;
```

</details>

</details>

## Black Diamond

1. Find the average length of the films.
    - use a sub query to find all the films that are longer than the average.
2. Using the `film` table display a count of how many movies there are of each rating.
3. Using the `payment` table display the average amount when checkout out by the employee with a `staff_id` of 2
4. Using the `payment` table, show the average total for each customer in ascending order.
5. Using the `rental` table, show how many times each `inventory_id` has been rented, order it by most rended to least rented.

## Contributions

If you see a problem or a typo, please fork, make the necessary changes, and create a pull request so we can review your changes and merge them into the master repo and branch.

## Copyright

© DevMountain LLC, 2017. Unauthorized use and/or duplication of this material without express and written permission from DevMountain, LLC is strictly prohibited. Excerpts and links may be used, provided that full and clear credit is given to DevMountain with appropriate and specific direction to the original content.

<p align="center">
<img src="https://s3.amazonaws.com/devmountain/readme-logo.png" width="250">
</p>