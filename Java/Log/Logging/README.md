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

ログのフォーマットを設定するオブジェクト。人間が読みやすいように成形することができる。
詳細な設定をpropertyファイル内で設定できるようで、その辺は今後の学習課題。

```Java
Formatter formatter =  new SimpleFormatter();
handler.setFormatter(formatter);
```

Sampleコード

```Java
SimpleFormatter formatter =  new SimpleFormatter();
handler.setFormatter(formatter);
```

### 出力するログレベルを設定する

Loggingが設定しているログレベルは以下の通り。

LogLevel|reference
--|--
FINEST | 非常に詳細なトレースメッセージ
FINER | かなり詳細なトレースメッセージ
FINE | 詳細なトレースメッセージ
CONFIG | 静的な構成メッセージ
INFO | 情報メッセージ
WARNING | 警告メッセージ
SEVERE | 重大なメッセージ

設定する時は、出力する最低レベルを指定する。INFOを指定すればログに出力されるのは、INFO、WARNING、SEVEREとなる。

```Java
logger.setLevel(Level.INFO);
```

## 実際に書いてみる

引用（一部微修正有）：　https://qiita.com/Qui/items/40077ce9e33738dd3914

```Java
public class BasicLoggingSample {

    public static void main(String[] args) throws SecurityException, IOException {
        // ロガーを取得してログレベルをINFOに設定
        Logger logger = Logger.getLogger(BasicLoggingSample.class.getName());
        logger.setLevel(Level.INFO);

        // ハンドラーを作成してロガーに登録
        Handler handler = new FileHandler("sample.log");
        logger.addHandler(handler);

        // フォーマッターを作成してハンドラーに登録
        SimpleFormatter formatter =  new SimpleFormatter();
        handler.setFormatter(formatter);

        // INFOメッセージを出力
        logger.log(Level.INFO, "INFOメッセージ");

        // それぞれのログレベルのメッセージを出力する簡易メソッドが用意されています。
        logger.finest("FINESTメッセージ");
        logger.finer("FINERメッセージ");
        logger.fine("FINEメッセージ");
        logger.config("CONFIGメッセージ");
        logger.info("INFOメッセージ");
        logger.warning("WARNINGメッセージ");
        logger.severe("SEVEREメッセージ");

        // メッセージは文字列で渡す方法の他に、Supplier<String>を渡す方法もあります。
        Supplier<String> supplier = new Supplier<String>() {
            @Override
            public String get() {
                return "Supplyメッセージ";
            }
        };
        logger.info(supplier);

        // Exceptionが発生した時のログ出力方法は以下の通り。引数に渡されたThrowableのスタックトレースが出力されます。
        logger.log(Level.WARNING, "エラーが発生したんだよ〜。", new RuntimeException("ランタイムエラー"));
    }
}
```

## 参考

[浦下.com　〜ITエンジニアの備忘録〜　Javaロガーとは？](https://urashita.com/archives/32595)

[java.util.loggingの使い方](https://qiita.com/Qui/items/40077ce9e33738dd3914)

[Java の標準ロギングAPI JUL(java.util.logger) を少しマシにする](https://blog1.mammb.com/entry/2017/02/24/070608)
