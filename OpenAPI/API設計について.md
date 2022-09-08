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
