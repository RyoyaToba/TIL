## HAVING句

> GROUP BYでグルーピングしたものからHAVING句での条件で絞り込みを行うもの

以下、達人に学ぶSQL徹底指南書を読んで学習した内容を自分なりにアウトプットしてまとめております。詳しくは[こちら](https://codezine.jp/article/detail/652)

### 応用1：データの歯抜けを探す

id|name
--|--
1|一郎
2|次郎
4|四郎

HAVING句の条件に
```
HAVING COUNT(*) <> MAX(id)
```
を設定

`COUNT(*)`はカラムに存在する行数を返す（上記だと3）
`MAX(id)`はidの最大値を返す（上記４）。  
そのため、２つが「イコールでないとき」という条件を付与できる。


### 応用２：最頻値を求める

TABLE: Student
name|score
--|--
一郎|30
次郎|20
三郎|30
四郎|10
五郎|10
六郎|10

GROUP BYで部分集合を作成するイメージを掴む

```SQL
SELECT score
FROM Student
GROUP　BY score
HAVING COUNT(*) >= All (
  SELECT COUNT(*)
  FROM Student
  GROUP BY score
 )
```

サブクエリの中の全てよりも（All）大きいものを指定。

### 応用３：Nullを含まない値を探す

```
COUNT(*)　　：　　　列の全ての行をカウントする
COUNT(列名)　　：　　　列ないのNullを除いた行をカウントする
```

これによって、HAVINGの条件の中で、Nullがあるかどうかの判別に使える











