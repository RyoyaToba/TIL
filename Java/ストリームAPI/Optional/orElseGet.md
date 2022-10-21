## orElseGet

固定的な値だけではなく、何らかの処理をしてその結果を戻したい場合には、orElseGetメソッドを使用する。

このメソッドは、引数としてSupplier型のラムダ式を受け取り、Optionalのインスタンスが空だった場合には、引数のラムダ式を実行してその結果を戻す。

```Java
public class GetSample{
  public static void main(String[] args){
    Optional<String> sample = Optional.empty();
    System.out.println(sample.orElseGet(() -> "else"));
  }
}
```
