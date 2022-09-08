## APIの設計

APIができる機能を洗い出す作業。

ToDoアプリケーションを例に取る。

## そのアプリケーションをつかって何ができるかを考える

**例：　ユーザーがタスクを管理できる**

## ②それを実現するためにはどのような機能が必要か

## HTTPメソッド　　URIと合わせてエンドポイントを作成する

method|path|contents
----|----|----
GET| / {path}|一覧取得
POST| / {path}|作成
GET| / {path} / : id|詳細取得
PUT| / {path} / : id|更新
DELETE| / {path} / : id|削除

## HTTPメソッドの冪等性と安全性

method| 冪等性 | 安全性
----|----|----
GET|Y|Y
PUT|Y|Y
DELETE|Y|N
POST|N|N

## リクエスト設計

**パスパラメータ**

/tasks/**999**

**クエリパラメータ**

/tasks?**title=bug**

リソースを一一意に特定できるかを考える。

**リクエストボディ**

{ title: "hoge" }

## レスポンス設計

**２xx**

Success

200

OK

201

Created

204

No Content

**3xx**

Redirection

**4xx**

Client Error

400

Bad Request

404

Not Found

**5xx**

Server Error

500

Internal Server Error

## タスク管理APIを例にしたAPI設計

### タスク作成

#### Request

- POST /tasks
  - body : 作成するタスクのJSON（e.g.{title: "hoge"}）
  
#### response
 
 - 201

    - header(location): 作成されたリソースのURI
    - body: 作成されたタスクのJSON（e.g.{id: 1, title: "hoge"}） 

 - 400
    - Bad Request
 
