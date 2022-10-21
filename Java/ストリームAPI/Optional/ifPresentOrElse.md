## ifPresentOrElse

ifPresentメソッドは、Optionalのインスタンスが値を保持していない場合は何も処理をしない。何か処理をしたい場合には、ifPresentOrElseメソッドを利用する。

このメソッドは、値がある場合は第一引数で指定したラムダ式（Consumer型）を実行し、値がない場合には第二引数で指定したラムダ式（Runnable型）を実行する。

```Java
public class IfPresentOrElseTest{
  public static void main(String[] args){
    Optional<String> sample = Optional.empty();
    sample.ifPresentOrElse(
      (str) -> System.out.println(str),
      () -> System.out.println("empty");
    )
  }
}
```
