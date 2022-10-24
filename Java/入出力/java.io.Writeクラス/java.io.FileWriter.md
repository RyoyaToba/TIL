## java.io.FileWriter

テキストファイルへの書き込みには、Writerサブクラスである、java.io.FileWriterクラスを使う。

このクラスにのコンストラクタには、出力先のファイル名を渡す。コンストラクタに指定した出力先のファイルが存在しない場合は、新たにファイルを作成する。

```Java
public class Sample{
  public static void main(String[] args) throws Exception{
    FileWriter out = new FileWriter("output.txt");
    try(out){
      out.write("Hello world!");
    }
  }
}
```

実行結果

```console
Hello world!
```

このコードを毎回実行すると、テキストファイルは上書きされる。続きに追記したい場合は、コンストラクタの第二引数にtrueを記述する。

```Java
public class Sample{
  public static void main(String[] args) throws Exception{
    FileWriter out = new FileWriter("output.txt", true);
    try(out){
      out.write("Hello world!");
    }
  }
}
```

実行結果

```console
Hello world!Hello world!
```

