## map

mapメソッドは、Function型の引数を受け取り、処理結果を持った新しいOptionalのインスタンスを生成し、その参照を戻す。

```Java
public class MapTest{
  public static void main(String[] args){
    Optional<String> sample = Optional.of("test");
    Optional<String> result = sample.map(
                      str -> str.toUpperCase());
    System.out.println(sample.get());
    System.out.println(result.get());
  }
}
```

