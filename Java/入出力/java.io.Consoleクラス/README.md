## java.io.Console

コンソールから入力を受け付けるには、java.lang.SystemクラスのInputStream型のinフィールドを利用する。このコードでは、バイト入力ストリームを扱うSystem.inのInputStreamを、文字入力ストリーム
を扱うReaderに変換するInputStreamReaderを経由して、バッファを利用した効率的なテキスト入力のためのBufferedReaderクラスのインスタンスを作っている。

```Java
public class UseSystemIn{
  public static void main(String[] args){
    try(BufferedReader br = new BufferedReader(
      new InputStreamReader(System.in))){
        String input = br.readLine();
        System.out.println(input);
    }
  }
}
```

このようなコードをより簡略化する目的で、JavaSE6からConsoleクラスが導入された。




