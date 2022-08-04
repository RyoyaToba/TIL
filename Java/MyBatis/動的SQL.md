## 動的SQLとは

MyBatisを使う利点の１つとして、この動的SQLを書くことができる点がある。条件によって、SQL文を多彩に変化させることができる仕組みが、MyBatisには備わっている。

### if

MyBatisでは、SQL文中でifタグを使うことで、条件分岐をつけることができる。JDBCの時、条件によってStringBuilderによってWHERE句を足していた時があったが、それをSQL上で実装できる。

```xml
<select id="findActiveBlogWithTitleLike"　　resultType="Blog">
  SELECT * FROM BLOG
    WHERE state = ‘ACTIVE’
  <if test="title != null">
    AND title like #{title}
  </if>
</select>
```

上記例文では、BLOGをACTIVEによって検索するSELECT文であるが、if文の条件で、「もしTitleがnullでなかったら、TiTleの条件」もついかしてくれというような記載がある。

①検索条件にTITLEがなかった場合
```SQL
  SELECT * FROM BLOG WHERE state = 'ACTIVE'
```

②検索条件にTITLEがあった場合
```SQL
  SELECT * FROM BLOG WHERE stata = 'ACTIVE' AND title like #{title}
```

もし、著者名を検索条件に加えたい場合であれば、以下のように、ifタグを追加してやれば良い。

```xml
<select id="findActiveBlogLike"　　resultType="Blog">
  SELECT * FROM BLOG WHERE state = ‘ACTIVE’
  <if test="title != null">
    AND title like #{title}
  </if>
  <if test="author != null and author.name != null">
    AND author_name like #{author.name}
  </if>
</select>
```

ここでこまるのは、WHERE句が全てif内に書かれている場合。つまり下のような例の時を考えてみる。

```xml
<select id="findActiveBlogLike"
     resultType="Blog">
  SELECT * FROM BLOG
  WHERE
  <if test="state != null">
    state = #{state}
  </if>
  <if test="title != null">
    AND title like #{title}
  </if>
  <if test="author != null and author.name != null">
    AND author_name like #{author.name}
  </if>
</select>
```

上記の例で、どの条件にも一致しない場合はどうなるか考える。そうすると、

```SQL
SELECT * FROM BLOG WHERE
```

また、２番目の条件のみが一致するような状態だとしたら、

```SQL
SELECT * FROM BLOG WHERE AND title like 'hoge'
```

のように、構文エラーとなってしまう。これを解決するために、WHEREタグを使うと良い。

```SQL
<select id="findActiveBlogLike"　　resultType="Blog">
  SELECT * FROM BLOG
  <where>
    <if test="state != null">
         state = #{state}
    </if>
    <if test="title != null">
        AND title like #{title}
    </if>
    <if test="author != null and author.name != null">
        AND author_name like #{author.name}
    </if>
  </where>
</select>
```

こいつのすごいところは、**内包するタグのどれかが結果を返すときだけ "WHERE" を挿入し、内包するタグから返された結果が "AND" または "OR" で始まっていた場合はこれを削除**することにある。

また、動作が期待と異なる場合は、trimを定義することで、処理内容を定義できる。

```xml
<trim prefix="WHERE" prefixOverrides="AND | OR >
</trim>
```

またこれは、動的なUpdate文を作成したいときにも効果を発揮し、

```xml
<update id="updateAuthorIfNecessary">
  update Author
    <set>
      <if test="username != null">username=#{username},</if>
      <if test="password != null">password=#{password},</if>
      <if test="email != null">email=#{email},</if>
      <if test="bio != null">bio=#{bio}</if>
    </set>
  where id=#{id}
</update>
```

set要素が余分なカンマを削除してくれる。


### choose when otherwise

多くの中から１つを条件として選択したい場合に有効なタグ。指定された条件によって、SQLが動的に変動する。

```xml
<select id="findActiveBlogLike"
     resultType="Blog">
  SELECT * FROM BLOG WHERE state = ‘ACTIVE’
  <choose>
    <when test="title != null">
      AND title like #{title}
    </when>
    <when test="author != null and author.name != null">
      AND author_name like #{author.name}
    </when>
    <otherwise>
      AND featured = 1
    </otherwise>
  </choose>
</select>
```

### foreach

コレクション要素をイテレーション処理したいときに使用する。例えば、IN演算子を使う場合など。ここはまだいまいちピンと来ていないので、調査中。

```xml
<select id="selectPostIn" resultType="domain.blog.Post">
  SELECT *
  FROM POST P
  <where>
    <foreach item="item" index="index" collection="list"
        open="ID in (" separator="," close=")" nullable="true">
          #{item}
    </foreach>
  </where>
</select>
```

### 参考
[MyBatis公式ドキュメント](https://mybatis.org/mybatis-3/ja/dynamic-sql.html)
