## What's  SQLBolt

> Welcome to SQLBolt, a series of interactive lessons and exercises designed to help you quickly learn SQL right in your browser.

[URL](https://sqlbolt.com/)


> Exercise 1 

1. Find the title of each film

```SQL
SELECT title FROM movies;
```

2. Find the director of each film

```SQL
SELECT director FROM movies;
```

3. Find the title and director of each film

```SQL
SELECT title, director FROM movies;
```

4. Find the title and year of each film

```SQL
SELECT title, year FROM movies;
```

5. Find all the information about each film

```SQL
SELECT * FROM movies;
```


> Exercise 2

1. Find the movie with a row id of 6

```SQL
SELECT * FROM movies WHERE id = 6;
```

2. Find the movies released in the years between 2000 and 2010

```SQL
SELECT * FROM movies WHERE year BETWEEN '2000' AND '2010';

```

3. Find the movies not released in the years between 2000 and 2010

```SQL
SELECT * FROM movies WHERE year NOT BETWEEN '2000' AND '2010';
```

4. Find the first 5 Pixar movies and their release year

自分の回答

表が見えていない場合もありますし、別解だと年が変わった時に対応できないので、私の回答がベストだと思います。
```SQL
SELECT * FROM movies ORDER BY year LIMIT 5;
```
別解（これでよいらしい）
```SQL
SELECT title, year FROM movies WHERE year <= 2003;
```


> Exercise 3

1. Find all the Toy Story movies

```SQL
SELECT * FROM movies WHERE title like '%Toy Story%';
```

2. Find all the movies directed by John Lasseter

```SQL
SELECT * FROM movies WHERE director = 'John Lasseter';
```

3. Find all the movies(and director) not ditected by John Lasseter

こっちのほうがよく見る
```SQL
SELECT * FROM movies WHERE director <> 'John Lasseter';
```

別解
```SQL
SELECT * FROM movies WHERE director != 'John Lasseter';
```

4. Find all the WALL-* movies

```SQL
SELECT * FROM movies WHERE title like 'WALL-%';
```


> Exercise 4

> Even though the data in a database may be unique, the results of any particular query may not be – take our Movies table for example, many different movies can be released the same year. In such cases, SQL provides a convenient way to discard rows that have a duplicate column value by using the DISTINCT keyword.

データの重複を削除する際に`DISTINCT`を用いる

1. List all directors of Pixar movies (alphabetically), without duplicates

```SQL
SELECT DISTINCT director FROM movies ORDER BY director;
```

> The LIMIT will reduce the number of rows to return, and the optional OFFSET will specify where to begin counting the number rows from.

LIMITは返される行数を制限する。OFFSETで行数のカウントを開始する場所を指定できる。

2. List the last four Pixar movies released (ordered from most recent to least)

```SQL
SELECT * FROM movies ORDER BY year DESC LIMIT 4;
```

3.  List the first five Pixar movies sorted alphabetically

```SQL
SELECT * FROM movies ORDER BY title LIMIT 5;
```

4. List the next five Pixar movies sorted alphabetically

```SQL
SELECT * FROM movies ORDER BY title LIMIT 5 OFFSET 5;
```

OFFSETの省略型

```SQL
SELECT * FROM movies ORDER BY title LIMIT 5, 5;
```

6番目から１０番目を選択したかったので、OFFSETは５を指定（indexとして１つ目が０番目なのだと）。

LIMITを省略してOFFSETのみを書くことはできない。　　


> Exercise 5 

1.  List all the Canadian cities and their populations

```SQL
SELECT city, population FROM North_american_cities WHERE country = 'Canada';
```

2. Order all the cities in the United States by their latitude from north to south

```SQL
SELECT * FROM North_american_cities WHERE country = 'United States' ORDER BY latitude DESC;
```

3. List all the cities west of Chicago, ordered from west to east

```SQL
SELECT * FROM North_american_cities WHERE longitude < -87.629798 ORDER BY Longitude;
```

 これはサブクエリをつかってもいいかもしれない

```SQL
SELECT * FROM North_american_cities 
WHERE 
longitude < (SELECT longitude FROM North_american_cities WHERE city = 'Chicago')
ORDER BY Longitude;
```

4. List the two largest cities in Mexico (by population)

```SQL
SELECT * FROM North_american_cities WHERE country = 'Mexico' ORDER BY population DESC LIMIT 2;
```

5. List the third and fourth largest cities (by population) in the United States and their population

```SQL
SELECT * FROM North_american_cities WHERE country = 'United States' ORDER BY population DESC LIMIT 2 OFFSET 2;
```


> Exercise 6

1. Find the domestic and international sales for each movie

```SQL
SELECT 
m.title
,b.domestic_sales
,b.international_sales
FROM
movies as m
JOIN
boxoffice as b
ON
m.id = b.movie_id
```

2. Show the sales numbers for each movie that did better internationally rather than domestically

```SQL
SELECT
*
FROM
movies as m
JOIN
boxoffice as b
ON
m.id = b.movie_id
WHERE
international_sales > domestic_sales
```

3. List all the movies by their ratings in descending order

```SQL
SELECT
*
FROM
movies as m
JOIN
boxoffice as b
ON
m.id = b.movie_id
ORDER BY
rating DESC;
```

デフォルトはINNER JOINになる


> Exercise ７

1. Find the list of all buildings that have employees

```SQL
SELECT DISTINCT building FROM employees;
```

2. Find the list of all buildings and their capacity

```SQL
SELECT * FROM buildings;
```

3. List all buildings and the distinct employee roles in each buiding (including empty buildings)

```SQL
SELECT DISTINCT
building_name
,role
FROM
buildings
LEFT OUTER JOIN
employees
ON
building = building_name;
```


> Exercise ８

1. Find the name and role of all employees who have not been assigned to a building 

```SQL
SELECT name, role FROM employees WHERE building IS NULL;
```

2. Find the names of the buildings that hold no employees

```SQL
SELECT
*
FROM
buildings
LEFT JOIN
employees
ON
buildings.building_name = employees.building
WHERE
employees.building IS NULL;
```


> Exercise ９

1. List all movies and their combined sales in millions of dollars

```SQL
SELECT title, (domestic_sales + international_sales) / 1000000 AS gross_sales_millions
FROM movies
JOIN boxoffice
ON movies.id = boxoffice.movie_id;
```

2. List all movies and their ratings in percent

```SQL
SELECT title, (rating * 10) as hyouka
FROM movies
JOIN boxoffice
ON movies.id = boxoffice.movie_id;
```

3. List all movies that were released on even number years

```SQL
SELECT title, year
FROM movies
JOIN boxoffice
ON movies.id = boxoffice.movie_id
WHERE year % 2 = 0;
```

> Exercise 10

1. Find the longest time that an employee has been at the studio

```SQL
SELECT max(years_employed) FROM employees;
```

2. For each role, find the average number of years employed by employees in that role

```SQL
SELECT role, avg(years_employed) FROM employees GROUP BY role;
```

3. Find the total number of employee years worked in each building

```SQL
SELECT building, sum(years_employed)
FROM employees
GROUP BY building;
```

> Exercise 11

1. Find the number of Artists in the studio (without a HAVING clause)

```SQL
SELECT count(*)
FROM employees
WHERE role = 'Artist';
```

2. Find the number of Employees of each role in the studio

```SQL
SELECT role, count(*)
FROM employees
GROUP BY role;
```

3. Find the total number of years employed by all Engineers

```SQL
SELECT role, sum(years_employed)
FROM employees
GROUP BY role
HAVING role = 'Engineer';
```


> Exercise 12

#### 実行順序

`FROM(JOIN)　→　WHERE　→　GROUP BY　→　HAVING →　SELECT　→　DISTINCT　→　ORDER BY　→　LIMIT（OFFSET）`

1. Find the number of movies each director has directed

```SQL
SELECT director, count(*) as mov_cut
FROM movies
JOIN boxoffice
ON movies.id = boxoffice.movie_id
GROUP BY director;
```

2. Find the total domestic and international sales that can be attributed to each director

```SQL
SELECT director, sum(domestic_sales + international_sales) as sales_total
FROM movies
JOIN boxoffice
ON movies.id = boxoffice.movie_id
GROUP BY director;
```


> Exercise 13

1.  Add the studio's new production, Toy Story 4 to the list of movies (you can use any director)

```SQL
INSERT INTO movies (id, title, director, year, length_minutes)
VALUES (15, 'Toy Story 4', 'John Lasseter', '2020', 100);
```

2. Toy Story 4 has been released to critical acclaim! It had a rating of 8.7, and made 340 million domestically and 270 million internationally. Add the record to the BoxOffice table.

```SQL
INSERT INTO boxoffice (movie_id, rating, domestic_sales, international_sales)
VALUES (15, 8.7, 3400000, 2700000);
```


> Exercise 14

1. The director for A Bug's Life is incorrect, it was actually directed by John Lasseter

```SQL
UPDATE movies SET director = 'John Lasseter' WHERE id = 2;
```

2. The year that Toy Story 2 was released is incorrect, it was actually released in 1999

```SQL
UPDATE movies SET year = '1999' WHERE id = 3;
```

3. Both the title and director for Toy Story 8 is incorrect! The title should be "Toy Story 3" and it was directed by Lee Unkrich

```SQL
UPDATE movies SET title = 'Toy Story 3', director = 'Lee Unkrich'
WHERE id = 11;
```


> Exercise 15

1. This database is getting too big, lets remove all movies that were released before 2005.

```SQL
DELETE FROM movies WHERE year < 2005;
```

2. Andrew Stanton has also left the studio, so please remove all movies directed by him.

```SQL
DELETE FROM movies WHERE director = 'Andrew Stanton';
```


> Exercise 16

1. Create a new table named Database with the following columns:
– Name A string (text) describing the name of the database
– Version A number (floating point) of the latest version of this database
– Download_count An integer count of the number of times this database was downloaded
This table has no constraints.

```SQL
CREATE TABLE Database(
Name TEXT,
Version FLOAT,
Download_count INTEGER
);
```


> Exercise 17

> As your data changes over time, SQL provides a way for you to update your corresponding tables and database schemas by using the ALTER TABLE statement to add, remove, or modify columns and table constraints.

ALTER　TABLEを利用することで、列とテーブルの制約を追加、削除、または変更することができる。

1. Add a column named Aspect_ratio with a FLOAT data type to store the aspect-ratio each movie was released in.

```SQL
ALTER TABLE movies
ADD COLUMN Aspect_ratio FLOAT
DEFAULT 2.39;
```

2. Add another column named Language with a TEXT data type to store the language that the movie was released in. Ensure that the default for this language is English.

```SQL
ALTER TABLE movies
ADD COLUMN Language TEXT
DEFAULT English;
```


> Exercise 18

1. We've sadly reached the end of our lessons, lets clean up by removing the Movies table

```SQL
DROP TABLE movies;
```

2. And drop the BoxOffice table as well

```SQL
DROP TABLE boxoffice;
```

