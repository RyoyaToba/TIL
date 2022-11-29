## Logging

> java.util.loggingは、Java標準のロギングライブラリです。
> java.util.loggingはLog4jを参考に作られましたが、ところどころ使いづらかったため、標準だったにも関わらず、log4jに置き換わることはできませんでした。

引用：　https://urashita.com/archives/32595

## 基本的な使い方

### Loggerのインスタンス化

ログ出力のためのオブジェクト、Loggerオブジェクト。

```Java
Logger logger = Logger.getLogger("loggerの名前")
```

Sampleコード

```Java
Logger logger = Logger.getLogger(BasicLoggingSample.class.getName());
```

### Handlerの設定

ログの出力先を制御するHandlerオブジェクト。

```Java
Handler handler = new FileHandler("C:\\sample\\sample.log");　// 出力先のパスを指定
logger.addHandler(handler);
```

Sampleコード

```Java
Handler handler = new FileHandler("sample.log"); // 同じディレクトリにsample.logというファイルでログを出力させる
logger.addHandler(handler);
```

### Formatterの設定

ログのフォーマットを設定するオブジェクト。



### 出力するログレベルを設定する





## 参考

[浦下.com　〜ITエンジニアの備忘録〜　Javaロガーとは？](https://urashita.com/archives/32595)

[java.util.loggingの使い方](https://qiita.com/Qui/items/40077ce9e33738dd3914)

[Java の標準ロギングAPI JUL(java.util.logger) を少しマシにする](https://blog1.mammb.com/entry/2017/02/24/070608)
