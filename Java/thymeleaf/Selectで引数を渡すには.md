目的：セレクトボックスを使って、選択されたものを引数としてメソッドに渡したい


やりたいことのイメージ

![レース検索 (1)](https://user-images.githubusercontent.com/105257856/185066697-32839c5b-1ca4-432b-b34f-56080ad06a2e.png)

選択されたものを引数で渡す場合は、若干誤解する部分があったので記録しておく。

簡単にいえば、nameを指定する場所はoptionタグ内ではなく、Selectタグ内に記述してくださいということです。Optionに設定していて、あれ？とばねーって何回もなったので。

```HTML
<select name="placeNum">
	<th:block th:each="place, status : ${placeList}">
		<option th:text="${place}" th:value="${status.count}">
		</option>
	</th:block>
</select>
```

