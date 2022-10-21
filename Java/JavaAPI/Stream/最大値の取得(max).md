## max

ストリーム内の要素を指定されたComparatorで並び替え、最大値を戻すメソッド。

```Java
public class MaxSample{
  public static void main(String[] args){
    List<Integer> list = Arrays.asList(98,99,96,97,95);
    Optional<Integer> result = 
      list.stream().max((a,b) -> {
      if(a == b) return 0;
      if(a < b) return -1;
      return 1;
    });
    result.ifPresent(System.out::println);
  }
}
```

Comparatorのcompareメソッドでは、並び替えのために2つの引数を比較する。最初の引数が2番目の引数よりも小さい場合は負の整数、両方が等しい場合は0、最初の引数が2番目の引数より大きい場合は性の整数
を戻すようにする。

このコードを実行すると、ストリーム内の数値が小さい順に並び、最大値を持ったOptionalクラスのインスタンスへの参照がもどされる。

実行結果

```console
99
```

