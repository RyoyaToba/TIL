## java.util.function

関数型インターフェイスはプログラマーが自由に定義することができるが、頻繁に使われるであろうものは、Java8より標準でjava.util.functionパッケージとして追加されている。



関数型インターフェイス|メソッド|説明
--|--|--
`Consumer<T>`|void accept(T)|引数を受け取って処理をする。結果を戻さない、引数の「消費者」
 `Supplier<T>`|T get()|何も受け取らずに結果だけを戻す「供給者」
 `Predicate<T>`|boolean test(T)|引数を受け取ってそれを評価する「断定」
 `Function<T>`|R apply(T)|引数を受け取って、指定された型（R）の結果を戻す「処理」

## Consumer

## Supplier

## Predicate

Predicateインターフェイスは、T型の型パラメータをうけとり、そのT型を受け取るtestメソッドにラムダ式を代入する。

```Java
public static void main(String[] args){
  Predicate<String> p = str -> {
    return " ".equals(str);
  };
  System.out.println(p.test(args[0]));
}
```

## Function

