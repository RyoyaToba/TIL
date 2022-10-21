## reduce

終端操作にはforEachだけでなく、「リダクション操作」と呼ばれる種類の処理がある。リダクション操作とは、一連の要素を一つにまとめる操作のこと。例えば、リスト内にある数値の合計を求める処理がリダクション操作である。

他にもリスト内の要素に何らかの処理を加え、その結果をリストにまとめるものもリダクション操作になる。

reduceメソッドはリダクション操作の1つで、値を累積的に結合していく関数を実行するためのもの。以下のコード例では1〜5の値を合計して出力している。

この場合の戻り値はOptionalである。

```Java
public class ReduceSample{
  public static void main(String[] args){
    List<Integer> list = Arrays.asList(1,2,3,4,5);
    Optional<Integer> result = list.stream().reduce((a,b) -> a + b);
    result.ifPresent(System.out::println);
  }
}
```

reduceメソッドはオーバーロードされているため、初期値を受け取るものも用意されている。例えば、次のコードではメソッドの第一引数に初期値として100という数値を渡している。

メソッドの第二引数には、これまでと同じように、BinaryOperator型のラムダ式を受け取っている。初期値がある場合、戻り値はInteger（int）型になる。

```Java
public class ReduceSample{
  public static void main(String[] args){
    int result = list.stream().reduce(100, (a, b) -> {
      int c = a + b;
      System.out.println("a = " + a);
      System.out.println(", b = " + b);
      System.out.println(", a + b = " + c);
      return c;
    });
    System.out.println(result);
  }
}
```

実行結果

```console
a = 100
, b = 1
, a + b = 101
a = 101
, b = 2
, a + b = 103
a = 103
, b = 3
, a + b = 106
a = 106
, b = 4
, a + b = 110
a = 110
, b = 5
, a + b = 115
115
```


