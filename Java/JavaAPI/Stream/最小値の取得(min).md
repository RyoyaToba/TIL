## min

最小値を取得するメソッド

```Java
public class MaxSample{
  public static void main(String[] args){
    List<Integer> list = Arrays.asList(98,99,96,97,95);
    Optional<Integer> result = 
      list.stream().min((a,b) -> {
      if(a == b) return 0;
      if(a < b) return -1;
      return 1;
    });
    result.ifPresent(System.out::println);
  }
}
```

並び替えのルールは、[maxメソッド](最大値の取得(max).md)の定義と同じなので、そちらを参照に。

実行結果

```console
95
```
