## supplier

処理途中の値を保持するためのオブジェクトを生成するメソッド。このメソッドは、引数を受け取らないが、戻り値が`java.util.function.Supplier型`のラムダ式でないといけない。

次のコードでは、ラムダ式の代わりにメソッド参照を用いて、StringBuilderのインスタンスを生成して戻すSupplier型の式として戻している。

```Java
@Override
public Supplier<StringBuilder> supplier {
  return StringBuilder::new;
}
```
