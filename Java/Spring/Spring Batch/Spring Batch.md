## Spring Batch

## バッチ処理とは

### 処理パターン１

あらかじめ登録した一連の処理を自動的に処理する処理方式（処理量は大小様々）

- スケジュール起動
- イベント起動
- オンラインディレート（REST API起動）

企業等の業務システムではこちらのパターンであることが多い

### 処理パターン2

大量データに対する処理といった重い処理を、一括して実施する

大規模シュミレータやAIの機械学習など


## Spring Batchとは

Spring Batchを使う利点

- バッチのユースケースを定義
- バッチの処理のテンプレートを提供
- 各処理を疎結合にしやすい
- よく使う機能（処理）は既にある
  - トランザクション処理
  - チャンクベースの処理
  - 宣言的I/O
  - 開始/停止/再起動
  - 再試行/スキップ
  - Webベースの管理インターフェイス（Spring Cloud Data Flow）

一般的なバッチ処理であれば、DB、ファイル、またはキューから大量のレコードを読み取り、何らかの方法でデータを処理し、変更された形式でデータを書き戻す。



## Spring Batchのアーキテクチャ

![Spring Batchアーキテクチャ](https://github.com/RyoyaToba/TIL/blob/main/documents/spring-batch-reference-model.png)

参照：https://spring.pleiades.io/spring-batch/docs/current/reference/html/job.html

### JobLauncher

Jobを起動する処理

### Job

１つ、複数のステップを順に実行する。

### Step

Itemreader（入力処理）、ItemProcessor（業務処理）、ItemWriter（出力処理）を繋げて実行する

### JobRepository

実行した結果を残してる部分

