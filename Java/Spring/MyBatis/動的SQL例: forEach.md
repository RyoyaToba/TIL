## forEachを使った動的SQL

forEachを使った動的SQL文を作成したので

```xml
<where>
　<if test="genderList.size != 0">
　　<foreach item="horseGender" collection="genderList" open="gender IN(" separator="," close=")">
   #{horseGender}
 </foreach>
</if>
<if test="name != ''">
  AND name LIKE CONCAT('%', #{name}, '%')
</if>
</where>
```

collectionは回したいCollection要素名、itemは取り出した１つ１つの要素につける変数。
