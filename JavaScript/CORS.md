## CORSとは

Cross-Origin-Resource Sharingの略で、クロスオリジンリソース共有と呼ばれる。オリジンを跨いだリソース共有という意味で、同一オリジンポリシーによって制限される。制限を破る形でのHTTPリクエストが制限される仕組みのこと。基本的に異なるオリジン間でのリソースの共有ができないようになっている仕組みのこと。これがブラウザに実装されているセキュリティーのためのメカニズムになっている。

## オリジンとは何か

`http://youtube.com：４３３`のようなyoutubeのURLがあったときに、`http`の部分をプロトコル（スキーム）、`youtube.com`の部分をドメイン、`:433`の部分をポート番号と呼ぶ。
これを合わせたもの（スキーム＋ドメイン＋ポート番号）をオリジンと呼ぶ。

## CORSの仕組み

APIなどで、外部のオリジンのデータを取得する場合、オリジンが異なるのでリソースの共有ができない。例えば先ほどのYoutubeのシステムから`http:twitter.com:433`のオリジンであるtwitterとで相互のデータやり取りをしようとする場合、オリジンが異なるのでデータのやり取りができない。これはWebが異なるオリジン間でのリソース共有を許可していないためである。

今回、ローカルサーバ内で住所を取得するzipCodaAPIを叩いたところ、CORSエラーが発生した。

`http://localhost:8080*` と　 `https://zipcoda.net/api`のオリジンが異なるために発生するエラーである。

```console
Access to XMLHttpRequest at 'http://zipcoda.net/api?zipcode=111-1111' from origin 'http://localhost:8080' has been blocked by CORS policy:
No 'Access-Control-Allow-Origin' header is present on the requested resource.
zipcoad.js:27 
```
