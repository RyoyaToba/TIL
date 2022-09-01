## 動的SQL_WHERE句

```xml
<select id="findRaceInfoByraceId" resultType="com.example.domain.RaceInfo">
		SELECT
		race_id
		,race_name
		,race_day
		,race_number
		,race_detail
		,feild
		FROM
		race_info
		<where>
			race_id like CONCAT(#{raceId}, '%')
			<if test="raceDay != null">
				AND race_day = #{raceDay}
			</if>
		</where>
</select>
```

メソッドfindRaceInfoByraceIdは、引数にraceIdとraceDayをとり、該当のraceInfoをDBから取得する。
その際、raceDayが指定されておらず、nullの場合もあるのだが、raceDayが指定されているときと、そうでない時でWHERE句を動的に変化させている。
