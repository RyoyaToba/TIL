目的：td要素にリンクを貼りたかった

こんな感じで、名前にリンクを貼りたかったのですが、テーブルの各要素に直接リンクを貼ることはできませんでした。つまり、td要素にaタグを貼れないんです。なので、td内にdivタグを設定して、そこにリンクを貼っています。


![レース検索 (2)](https://user-images.githubusercontent.com/105257856/185070349-6210eb2c-e023-414d-9735-247b39e03845.png)




```HTML
<tr th:each="raceResult, status : ${raceResultList}">
		<td th:id="rank + ${raceResult.rank}" th:text="${raceResult.rank}"></td>
		<td th:class="waku + ${raceResult.waku}" th:text="${raceResult.waku}"></td>
		<td th:text="${raceResult.horseNumber}"></td>
		<td><a th:href="@{/horse/horse-detail/?(name=${raceResult.horseName})}">
					<div th:text="${raceResult.horseName}"></div>
			  </a></td>
		<td th:text="${raceResult.gender}"></td>
		<td th:text="${raceResult.age}"></td>
		<td th:text="${raceResult.jockeyWeight}"></td>
		<td th:text="${raceResult.jockeyName}"></td>
		<td th:text="${raceResult.raceTime}"></td>
</tr>
```
