## Charsetクラス

Java SE 9から、ISO-8859-1の他に、**UTF-8**で保存されたプロパティファイルも扱えるようになった。
UTF-8では、日本語をはじめとした多種多様な言語を扱うことができるので、native2asciiコマンドでUnicode形式に変換する必要がない。

```java
public static void main(Sring[] args) {
  Properties prop = new Properties();
  prop.load(new FileReader(
            "sample.properties",
            Charset.forName("UTF-8")));
  System.out.println(prop.getProperty("test"));
}
```

特定の文字セットを扱うCharsetのインスタンスを取得するには、コード例のようにforNameメソッドに文字コード名を渡す。
そのインスタンスへの参照をFileReaderクラスのコンストラクタの第二引数に渡すことで、指定した文字コードでプロパティファイルが読み込まれる。

