## CASE式

SQLで書くことができる条件分岐式。

prefecture

id|pref_name|
--|--
1|青森県
2|秋田県
3|石川県
4|埼玉県
5|沖縄県

## 基本的な使い方

`CASE [カラム名] WHEN [条件１] THEN [処理１]`

所謂単純CASE式と呼ばれるのがこの表記方法

```SQL
SELECT *,
  CASE pref_name
    WHEN '青森県' THEN '東北'
    WHEN '秋田県' THEN '東北'
    WHEN '石川県' THEN '北陸'
    WHNE '埼玉県' THEN '関東'
  ELSE 'それ以外'
  END
FROM prefecture
```

id|pref_name|case
--|--|--
1|青森県|東北
2|秋田県|東北
3|石川県|北陸
4|埼玉県|関東
5|沖縄県|それ以外

検索CASE式で書きなおすと下記のようになる。

`CASE WHEN [条件１] THEN [処理１]`

```SQL
SELECT *,
  CASE
    WHEN pref_name = '青森県' THEN '東北'
    WHEN pref_name = '秋田県' THEN '東北'
    WHEN pref_name = '石川県' THEN '北陸'
    WHNE pref_name = '埼玉県' THEN '関東'
  ELSE 'それ以外'
  END
FROM prefecture
```

## CASE式を入れ子にする

複数の条件分岐を使った書き方もできる。次のように、

idが奇数で、名前が青森県の時に東北と表示を行う表記であれば・・・

```SQL
SELECT
   *,
    CASE 
        WHEN id % 2 = 1 THEN
             CASE pref_name
                 WHEN '青森県' THEN '東北'
                 ELSE '偶数だけど、それ以外'
             END
        ELSE '奇数でもないし、それ以外だし'
    END
FROM prefecture;
```

id|pref_name|case
--|--|--
1|青森県|東北
2|石川県|奇数でもないし、それ以外だし
3|埼玉県|偶数だけど、それ以外
4|沖縄県|奇数でもないし、それ以外だし


## 参考

https://tech-blog.rakus.co.jp/entry/20221004/case

https://mickindex.sakura.ne.jp/database/db_case.html
