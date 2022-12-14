## DOMA

> Doma は Java のDBアクセスフレームワークです。
>
> Doma のバージョンには 1 と 2 がありますが、 このドキュメントは バージョン 2 を対象としています。
>
> Doma 2 には以下の特徴があります。
>
> * 注釈処理を使用して コンパイル時 にコードの生成やコードの検証を行う
> * データベース上のカラムの値を振る舞いを持った Java オブジェクトにマッピングできる
> * 2-way SQL と呼ばれる SQL テンプレートを利用できる
> * Java 8 の java.time.LocalDate や java.util.Optional や java.util.stream.Stream を利用できる
> * JRE 以外のライブラリへの依存が一切ない
> * このドキュメントは複数のセクションから成ります。

## サンプルプロジェクトの構成

```
─ src
  ├── main
  │   ├── java
  │   │   └── boilerplate
  │   │       ├── AppConfig.java
  │   │       ├── dao
  │   │       │   ├── AppDao.java
  │   │       │   └── EmployeeDao.java
  │   │       └── entity
  │   │           └── Employee.java
  │   └── resources
  │       └── META-INF
  │           └── boilerplate
  │               └── dao
  │                   ├── AppDao
  │                   │   ├── create.script
  │                   │   └── drop.script
  │                   └── EmployeeDao
  │                       ├── selectAll.sql
  │                       └── selectById.sql
  └── test
      ├── java
      │   └── boilerplate
      │       ├── DbResource.java
      │       └── dao
      │           └── EmployeeDaoTest.java
      └── resources
```

### AppConfig.java
Doma を実行するために必要な 設定 です。

### AppDao.java

このアプリケーションで利用するデータベースのスキーマを実行時に作成/破棄するユーティリティです。 実環境では不要になります。 スキーマの作成と破棄には META-INF/boilerplate/dao/AppDao/ 以下のスクリプトファイルを使用します。

### Employee.java

データベースの EMPLOYEE テーブルに対応する エンティティクラス です。

### EmployeeDao.java

Employee クラスの取得や更新などを行う Daoインタフェース です。 META-INF/boilerplate/dao/EmployeeDao/ 以下の SQLファイル を使用します。

### EmployeeDaoTest.java

EmployeeDao を使ったテストです。 このファイルにテストケースを追加しながら Doma の学習ができます。 テストメソッドごとにデータベーススキーマの作成と破棄を行っているため データの更新によって他のテストが影響を受けることはありません。


## 参考

https://doma.readthedocs.io/en/2.19.2/
