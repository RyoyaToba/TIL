## APIとは

参照：https://www.youtube.com/watch?v=HqvcmkFjVnw

Application Programming Interfaceの略。他社が提供するサービス内の情報や機能を扱えるようにする仕組み。

例：ぐるなびAPI：「新宿」「食事」などでリクエストを投げると、新宿駅周辺の飲食店の情報を返してくれる。

## Web APIとは

HTTP/HTTPSベースで実現するAPIのことで、現状APIと言われたらこのWebAPIのことを指すのが一般的。

## RESTful APIとは

RESTの原則に沿って実装されているAPIのこと。APIを効率的に活用するためのもので、多くのAPIで用いられている原則・ルールのこと。

RESTとは、REpresentational State Transferの略。以下の４つの法則を満たして実装されている。

### アドレス可能性

全ての情報が一意なURIで表現されるようにすること。1つのURI（URLの広い概念）で全ての機能を表現できるようにすること。

### ステートレス性

全てのリクエストが完全に分離していて、セッションなどの状態管理は行われないこと。１回目のリクエストと２回目のリクエストは完全に独立しており、影響を及ぼさない。

### 接続性

情報に「別の情報へのリンク」を含めることができる。それにより、別の情報へ接続することができる。

### 統一インターフェイス

情報の取得、作成、更新、削除といった操作一式は全てHTTPメソッドを利用している。
