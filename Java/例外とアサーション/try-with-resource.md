## try-with-resource

try-with-resourceはJavaSE7で導入された機能で、プログラム中で扱うリソースを自動的に閉じるためのもの。

リソースは、使う時に開き、使い終わったら閉じなければならない。リソースを使い終わったら閉じるのは必須ではなく、任意であるため、プログラマーが書き忘れる可能性がある。
それを防止するためにJavaSE7からtry-with-resourceが導入された。

**try-with-resource以前の文**

```Java
try {
  // hoge
} catch (Exception e){
  // hoge
} finally {
  try {
    if (con != null) {
      con.close();
    }
  } catch {
    throw new Exception(e);
  }
}
```

このコードのように、finallyブロックでリソースを閉じるために、try-catchを入れ子に書かないといけなかった。

**try-with-resource**

```Java
try (Connection con = DBManager.createConnection()) {
  // hoge
} catch (Exception e){
  // hoge
}
```

try-with-resourceの目的は例外処理ではなく、リソースの閉じ忘れを防ぐことが目的なので、catchブロックとfinallyブロックは省略することが可能。

try-with-resource文で処理できるのは、`java.lang.AutoCloseableインターフェイス`、もしくは、`java.io.Closeableインターフェイス`を実装したクラス。

**AutoCloseableを実装したクラス**

```Java
public class SampleResource implements AutoCloseable {
  @Override
  public void close() throws Exception {
    System.out.println("close");
  }
}
```

**Closeableを実装したクラス**

```Java
public class SampleResource implements Closeable {
  @Override
  public void close() throws IOException {
    System.out.println("close");
  }
}
```

