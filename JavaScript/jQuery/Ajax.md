## ajax

> AjaxとはAsynchronous JavaScript + XMLの略で、JavaScriptとXMLを使用して行われる非同期処理を行うことができる技術。

## Ajaxの基本的な使い方

AjaxはJSで使うことが主流だったが、昨今はjQueryで記述することの方がメジャーである。またfetchAPIなるものを使って通信することが最近は多いようで、そちらに関してはまた調べる。

基本的な使い方は以下の通り

```JavaScript
`use strict`
$.ajax({
url: 'http://localhost:8080/search/count', //接続するURL
type: 'post', //接続形式
dataType: 'json', //受けとるデータ型
data: { // dataを記述　HTMLから取得した値をControllerに送る
	name: nameText.value,
	father: fatherText.value,
	mother: motherText.value,
	genderArray: genderArray.toString()
	},
async: true
})
.done(function(data) { // 成功した時
	document.getElementById('search-count').innerText = data.count + "件ヒットしました"
	console.log("target")
	})
	.fail(function() { //失敗した時
	console.log('fail')
	})
}
```

Contoroller側も記載する

```Java
RestController //APIのときと同じ。viewを返さない時はこのアノテーションを付与
@RequestMapping("/search")
public class CountSearchController {

	@Autowired
	private HorseProfileService horseProfileService;

	@ResponseBody //JSにこの要素を返すことを示す
	@RequestMapping(value = "/count", method = RequestMethod.POST)
	public Map<String, Integer> searchCount(String name, String father, String mother, String[] genderArray) {
		//引数がAjaxのdataで指定されたものになる。
		System.out.println("通信できてるよ"); //確認用
		List<String> genderList = Arrays.asList(genderArray);
		
		Integer count = horseProfileService.load(name, father, mother, genderList).size();
		Map<String, Integer> countMap = new HashMap<>();
		countMap.put("count", count);
		
		return countMap; //JSONで返すので、Mapにする
	}
}
