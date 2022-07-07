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
```SQL
SELECT * FROM movies ORDER BY year LIMIT 5;
```
別解（これでいいんかい）
```SQL
SELECT title, year FROM movies WHERE year <= 2003;
```










