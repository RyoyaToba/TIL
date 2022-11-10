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
```

## 実装例

アンケートプラットフォーム作成におけるAjax利用

```JavaScript
'use strict'
    // 編集のFormボタン
    let editBtn = document.getElementById('edit-btn');
    // sessionに入っている管理者のemailをhiddenから取得
    let adminEmail = document.getElementById('adminEmail');
    // sessionに入っている管理者のversionNumberをhiddenから取得
    let adminVersionNumber = document.getElementById('adminVersionNumber').value;
    // jsonから戻されるDB上のversionNumberを格納する変数
    let DBsavedNumber;
            
    // 登録ボタンが押された時、登録確認アラートを表示する
    editBtn.onclick = editCheck;

//　確認アラートを表示させる関数
function editCheck(){
    // Formに入力された名前
    let name = document.getElementById('name');
    // Formに入力されたメールアドレス
    let email = document.getElementById('email');
    // Formに入力されたパスワード
    let password = document.getElementById('password');
    // 編集フォームを取得
    let editForm = document.getElementById('edit-form');
    // 確認アラート表示
    const result = confirm("名前：" + name.value 
                            + "\nメールアドレス：" + email.value
                            + "\nパスワード：" + password.value
                            + "\nこの内容に変更します。よろしいですか？");
    // 確認アラートの結果による分岐処理
    if (result){ // 更新するを選択した場合、Ajax関数を呼び、DBに格納されているversionNumberを取得
        checkVersionNumber()
        // 確認用
        console.log(DBsavedNumber);
        console.log(adminVersionNumber);
       
        if (DBsavedNumber == adminVersionNumber){ // versionNumberの一致
            alert("変更しました");
        } else { // versionNumber不一致なら、既に別ユーザーに更新されているので、再度ログインを促す
            alert("変更に失敗しました。再度ログインし直してください");
            editForm.action = 'http://localhost:8080/admin/login';
        }
    } else { // 登録情報の変更をキャンセルした場合、再度入力を促す
        alert('登録情報を変更してください')
        editForm.action = 'http://localhost:8080/admin/menu';
    }
}

// DBに保存されているversionNumberを非同期で取得するAjax関数
const checkVersionNumber = () => {
    $.ajax({
        url: 'http://localhost:8080/admin/checkVersionNumber',
        type: 'post',
        dataType: 'json',
        data: {
            email: adminEmail.value,
        },
        async: false
    })
        .done(function(data){
            console.log("success!") 
            DBsavedNumber = data.savedVersionNumber; // 事前に宣言した変数に格納。上のIf条件で使用
        })
        .fail(function(){
            console.log('fail');
        })
}
```
