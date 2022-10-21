## orElseThrow

Optionalが空だった場合に、意図的に例外を発生させるにはorElseThrowを使用する。このメソッドは、例外やエラーのスーパークラスであるThrowable型を戻すSupplier型のラムダ式を引数にして受け取る。

```Java
public class GetTest{
  public static void main(String[] args){
    Optional<String> sample = Optional.empty();
    System.out.println(
      sample.orElseThrow(() -> new Exception()));
  }
}
```
