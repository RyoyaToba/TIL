## ifPresent

Optionalから値を取り出さずに処理したい場合にifPresentメソッドを使用する。このメソッドはConsumer型のラムダ式を受け取り、Optionalが値を持っていれば引数に渡してラムダ式を実行する。

以下の例では、Optionalに文字列を設定し、ifPresentメソッドで出力している。

```Java
public class Sample{
  public static void main(String[] args){
    Optional<String> sample = Optional.of("test");
    sample.ifPresent((str) -> System.out.println(str));
  }
}
```
