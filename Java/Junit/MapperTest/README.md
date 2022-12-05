## AssertJとDbSetupを使ったテスト

### AssertJ

[公式リファレンス](https://assertj.github.io/doc/)

AssertJ はいくつかのモジュールで構成されています。

* JDK タイプ (文字列、イテラブル、ストリーム、パス、ファイル、マップなど) のアサーションを提供するコアモジュール
* Guava タイプのアサーションを提供する Guava モジュール (マルチマップ、オプション… )
* Joda Time タイプ (DateTime、LocalDateTime) のアサーションを提供する Joda Timeモジュール
* Neo4J タイプ (パス、ノード、リレーションシップなど) のアサーションを提供するNeo4Jモジュール
* リレーショナル データベース タイプ (テーブル、行、列など) のアサーションを提供するDBモジュール
* Swing モジュールは、Swing ユーザー インターフェイスの機能テスト用のシンプルで直感的な API を提供します。

AssertJ は、豊富なアサーション セットと本当に役立つエラー メッセージを提供し、テスト コードの読みやすさを改善し、お気に入りの IDE 内で非常に使いやすいように設計された Java ライブラリです。

[Javadoc](https://www.javadoc.io/doc/org.assertj/assertj-core/latest/index.html)は最新バージョンです。各アサーションが説明されており、そのほとんどにコード例が含まれているので、必要に応じて確認してください。

### DbSetup



