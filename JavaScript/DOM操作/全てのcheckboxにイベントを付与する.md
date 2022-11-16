## チェックボックスにイベントを付与する

まとめて行う方法を紹介。

```JavaScript
// 全てのInputタグからcheckboxを指定してとりだす
	for (let input of allInput) {
		if (input.type == 'checkbox') {
			allCheckBox.push(input);
		}
	}

	// 全てのチェックボックスの変化に応じてAjaxを呼ぶ
	for (let checkBox of allCheckBox) {
		checkBox.addEventListener('change', function() {
			searchCount();
			console.log(genderArray)
		})
	}
```

非常に便利
