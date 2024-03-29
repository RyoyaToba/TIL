## Spring Batch

SpringBatchの練習に使ったコードは以下に記載

https://github.com/RyoyaToba/springBatchChunkCsvInport

https://github.com/RyoyaToba/springBatchChunkCsvExport

https://github.com/RyoyaToba/springBatch_HelloWorldTasklet

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

バッチアプリケーションを起動するためのインターフェイス。すべてのバッチアプリケーションはこのクラスから処理が開始する。バッチアプリケーションへ引数を渡すことも可能。
JobLauncherを利用者が直接利用することも可能だが、JavaコマンドからCommandLineJobRunnerを起動することでより簡単にバッチ処理を開始させることができる。
CommandLineJobRunnerは、JobLauncharを起動するための各種処理を引き受けてくれる。

### Job

Spring Batchにおけるバッチアプリケーションの一連の処理をまとめた１実行単位。

### Step

Jobを構成する処理の単位。１つのJobに１〜N個のStepを持たせることが可能。１つのJobの処理を複数のStepに分割することにより、処理の再利用化、並列化、条件分岐といった制御が可能になる。
Stepは、チャンク方式かタスクレット方式のいずれかの方式で実装する。いずれもSpring　Batchが定義する方式である。

**チャンクモデル**

Itemreader（入力処理）、ItemProcessor（業務処理）、ItemWriter（出力処理）を繋げて実行する

**タスクレットモデル**

チャンクモデルとは異なり、自由に処理を記述できる方式。チャンクモデルの型に当てはまらない処理を実装したい場合、タスクレットモデルを使う

### ItemReader ItemProcessor ItemWriter

Stepの処理を、データの入力・加工・出力の３つに分割するためのインターフェイス。バッチアプリケーションは、この３パターンの処理で構成されることが多いことに由来し、Spring Batchでは主にチャンク方式でこれらの
インターフェイスの実装を活用する。利用者はビジネスロジックをそれぞれぼ役割に応じて分散して記述する。データの入出力を担うItemReaderとItemWriterは、データベースやファイルからJavaオブジェクトへの変換、もしくはその逆の処理であることが多いため、Spring Batchから標準な実装が提供されている。ファイルやデータベースからデータの入出力を行う一般的なバッチアプリケーションの場合は、Spring Batchの標準実装をそのまま使用するだけで要件を満たせるケースもある。

### JobRepository

JobやStepの状況を管理する機構。これらの管理情報は、Spring Batchが規定するテーブルスキーマをもとにデータベース上に永続化される。





