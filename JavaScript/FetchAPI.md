## FetchAPI

> Fetch APIはリソース取得のためのインターフェイスを提供しています。
> XMLHttpRequestと似たようなものではありますが、より強力で柔軟な操作が可能です。

## jQueryとの違い

> fetch() から返されたプロミスは、レスポンスが HTTP 404 や 500 であっても、 HTTP エラーステータスで拒否されません。代わりに、正常に解決され (ok ステータスが false に設定されます)、ネットワーク障害が発生した場合、または要求の完了が妨げられた場合にのみ拒否されます。fetch() は資格情報の初期化オプションを (include に) 設定しない限り、オリジンをまたいだ Cookie を送信しません。


## GET

住所検索API zipcodaを用いて、GETメソッドをFetchAPIで実行する

```JavaScript
const searchAddressFetch = () => {

 let zipcode = document.getElementById('zipcode');

  const params = new URLSearchParams({ zipcode: zipcode.value });
　　　　　
  
	fetch('https://zipcoda.net/api?' + params)　 // 第一引数に接続するURLを設定
		.then(response => response.json())　　　　　　　　　　　　　 // Responseの形式をJSONに変換 
		.then(data => console.log(data.items))   // dataの処理 

	console.log("https://zipcoda.net/api?" + params)　 // 確認用
}
```

比較のために、従来のjQueryでのコードを下に示す

```JavaScript
const searchAddressAjax = () => {
let zipcode = document.getElementById('zipcode');

$.ajax({
  url: 'http://zipcoda.net/api',
  type: 'GET',
  dataType: 'jsonp',
  data: {
    zipcode: zipcode.value
  },
  async: true
  })
  .done(function(data) {
     console.log(data);
     document.getElementById('prefecture').value = data.items[0].pref;
     document.getElementById('city').value = data.items[0].address;
  })
  .fail(function(XMLHttpRequest) {
     console.log('XMLHttpRequest:' + XMLHttpRequest.status);
  });
}
```


参考： [FetchAPI公式リファレンス](https://developer.mozilla.org/ja/docs/Web/API/Fetch_API)
