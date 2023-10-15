## native2ascii

プロパティファイルへの変換を行うには**native2ascii**というjavaの標準ツールを利用する。

java.util.Propertiesクラスを利用すると、プロパティファイルに記述した文字列は、文字コードがISO-8859-1として読み込まれる。この文字コードは、ラテンアルファベット文字や一部の記号を合わせて計191字を規定したもので、日本語は扱うことができない。
そのため、日本語を扱いたい場合には、日本語からUnicode表記に変換するnative2asciiというjavaの標準ツールを利用する。

* test.txt
```java
hello=こんにちは
```

このテキストファイルをプロパティファイルに変換するには、native2asciiを用いる。
次のコマンドは、test.txtを読み込んで、日本語の文字列をUnicode表記に変換してからtest.propertiesとしてファイルに出力する。

```java
native2ascii test.txt test.properties
```

