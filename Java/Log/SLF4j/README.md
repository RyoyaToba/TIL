## [Logback](#)と[SLF4j](https://www.slf4j.org/download.html)

LogbackとSLF4j(以下まとめてLogbackと呼ぶ)はSpringBootであればデフォルトで装備されている。
SpringBootを使わない場合は、外部jarをダウンロードする必要がある。

## 基本的な使い方

以下のコード例のように、LoggerFactoryを利用してLoggerインターフェイスを生成する。

```Java
Logger logger = LoggerFactory.getLogger(SampleController.class);
```

SpringBootでは、Controller内でloggerを呼び出すと以下のように記述すれば、コンソール上にログが出力される。

```Java
@GetMapping("sample")
  public String get() {
    logger.info("access GET sample");
```

コンソール出力結果

```console
2021-04-23 10:00:00.235  INFO 28304 --- [nio-8080-exec-2] app.controller.SampleController     : access GET sample
```

## ログレベル

Logback には、TRACE、DEBUG、INFO、WARN、ERRORの順でログレベルが存在する。

SpringBootでは、デフォルトでINFOが設定されているので、特に変更をしなければDEBUG、以下は出力されない。

## フォーマット

出力メッセージには、`{}`を利用することで、変数を格納することができる。

```Java
String name = "hoge";
logger.info("name is {}", name); // name is hoge
```

複数の変数を設定することもできる。

```Java
String name = "hoge";
Integer age = 27; 
logger.info("name is {}. age is {}", name, age); // name is hoge. age is 27
```

## スタックトレース

スタックトレースを出力したい場合は、例外インスタンスを引数に指定する。

```Java
try {
  //...
} catch (Exception e) {
  logger.error("system error", e);
}
```

## 設定

application.ymlファイルに詳細な設定を記述しておくこともできる。

プロパティ|デフォルト値|説明
--|--|--
logging.level.root|info|ルートのログレベル
logging.file.name|	|ログファイルのパス
logging.file.path|	|ログファイルの出力先フォルダパス logging.file.nameが優先される
logging.pattern.dateformat|yyyy-MM-dd HH:mm:ss.SSS|ログの日付フォーマット
logging.pattern.console|省略|コンソール出力における出力パターン
logging.pattern.file|省略|ファイル出力における出力パターン
logging.logback.rollingpolicy.clean-history-on-start|false|アプリケーションの起動時にアーカイブを削除するかどうか
logging.logback.rollingpolicy.file-name-pattern|${LOG_FILE}.%d{yyyy-MM-dd}.%i.gz|アーカイブファイル名のパターン
logging.logback.rollingpolicy.max-file-size|10MB|ログファイルの最大サイズ
logging.logback.rollingpolicy.max-history|7|アーカイブ日数
logging.logback.rollingpolicy.total-size-cap|0B|ログバックアップの合計サイズ

## パターンレイアウト

ログの出力パターンは、以下のパターンレイアウトを使用して設定する。

### 変換指定子

日付など、特定の値を表す文字で、`%`を先頭につける。

文字|例|説明
--|--|--
c, lo, logger	| %c, %c{0}	| Logger生成時に指定したクラスまたはロガーの名前
d, date	| %d{yyyy-MM-dd HH:mm:ss.SS} | 日時
m, msg, message	| %m |	logger.info()などで指定したメッセージ
n | %n | 改行
p, le, level | %p | ログレベル
replace	| %replace(%m){'\s', ''} | 文字の置換

### 書式修飾子

変換指定子の出力する文字数を制限するためのもので、 最小値.最大値のように表現し、%と文字の間に記述する。

また書式修飾子は、()を使ってグループ化した文字に対して指定することもできる。 ()を使用したい場合は、\でエスケープする。

## 参考

https://urashita.com/archives/32595

https://logback.qos.ch/

https://qiita.com/NagaokaKenichi/items/9febd2e559331152fcf8

https://b1san-blog.com/post/spring/spring-log/
