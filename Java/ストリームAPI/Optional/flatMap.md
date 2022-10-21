## flatMap

以下のコードのように、calcメソッドの戻り値がOptionalなので、呼び出し元のmainメソッド内に、mapメソッドの呼び出しで変数bにOptionalが入れ子で入ってしまうため、コンパイルエラーになる。

mapメソッドは新しいOptionalを生成し、その中に戻り値を格納するが、flatMapは、戻り値をOptionalに入れずにそのまま戻すメソッド。

```Java
public class Test{
  public static void main(String[] args){
    Optional<Integer> a = Optional.of(100);
    
    // コンパイルエラー　bにOptional<Optional<Integer>>を代入しようとしている
    Optional<Integer> b = a.map(price -> calc(price,3));
    System.out.println(b.get());
  }
 
 // 戻り値がOptional<Integer>型
 private static Optional<Integer> calc(int price, int qty){
  if (qty < 0){
    return Optional.empty();
  }
  return Optional.of(price * qty);
 }
}
```
