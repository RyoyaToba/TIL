## Set

java.util.Setインターフェイスは、重複する要素を持たないことを保証するコレクション機能を定義している。

重複する要素とは、equalsメソッドで等しいと判断される要素のこと。

このインターフェイスのもう1つの特徴は、順序を規定しないこと。Listのように入れた順序の通りには要素が並ぶことはない。

## HashSet

実現クラスであるHashSetクラスは、要素の並び順を保証しない。

```Java
public class Main {
    public static void main(String[] args) throws Exception{
      Set<String> set = new HashSet<>();
      set.add("B");
      set.add("D");
      set.add("A");
      set.add("C");
      set.add("A");

      set.stream().forEach(System.out::println);
    }
}
```

実行結果

```console
A
B
C
D
```

## TreeSet

実現クラスであるTreeSetクラスは、自然順で並び替えるか、引数で渡されたComparatorのアルゴリズムに従う。


```Java
public class Main {
    public static void main(String[] args) throws Exception{
      Set<String> set = new TreeSet<>();
      set.add("B");
      set.add("D");
      set.add("A");
      set.add("C");
      set.add("A");

      set.stream().forEach(System.out::println);
    }
}
```

実行結果

```console
A
B
C
D
```
