## What`s  SQLBolt?

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
別解（これでいいんかい）
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











