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


## 参考

https://urashita.com/archives/32595

https://logback.qos.ch/

https://qiita.com/NagaokaKenichi/items/9febd2e559331152fcf8

https://b1san-blog.com/post/spring/spring-log/
