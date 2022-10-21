## orElse

引数に代替値を指定することができるメソッドであり、Optionalに値が存在すればその値を、存在しないのであれば代替値を戻り値として戻す。

以下のコードでは、OptionalにAという文字列を代入しているので、orElseメソッド内の代替値Bは出力されず、Aが出力される。

```Java
public class Sample{
  public static void main(String[] args){
    Optional<String> sample = Optional.of("A");
    System.out.println(sample.orElse("B")); // A
  }
}
```




