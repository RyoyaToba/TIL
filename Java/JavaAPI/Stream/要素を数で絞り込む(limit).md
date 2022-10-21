## limit

要素を引数で渡した数によって絞り込むにはlimitを使用する。

```Java
public class LimitSample{
  public static void main(String[] args){
    List<Integer> list = Arrays.asList(1,2,3,4,5,6,7,8,9,10);
    list.stream()
        .limit(5)
        .forEach(System.out.println);
  }
}
```

出力結果

```console
1
2
3
4
5
```
