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






