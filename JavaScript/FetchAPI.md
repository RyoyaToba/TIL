## FetchAPI

> Fetch APIはリソース取得のためのインターフェイスを提供しています。
> XMLHttpRequestと似たようなものではありますが、より強力で柔軟な操作が可能です。

## jQueryとの違い

> fetch() から返されたプロミスは、レスポンスが HTTP 404 や 500 であっても、 HTTP エラーステータスで拒否されません。代わりに、正常に解決され (ok ステータスが false に設定されます)、ネットワーク障害が発生した場合、または要求の完了が妨げられた場合にのみ拒否されます。

> fetch() は資格情報の初期化オプションを (include に) 設定しない限り、オリジンをまたいだ Cookie を送信しません。


参考： [FetchAPI公式リファレンス](https://developer.mozilla.org/ja/docs/Web/API/Fetch_API)
