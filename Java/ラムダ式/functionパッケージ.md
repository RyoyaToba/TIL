## java.util.function

関数型インターフェイスはプログラマーが自由に定義することができるが、頻繁に使われるであろうものは、Java8より標準でjava.util.functionパッケージとして追加されている。



関数型インターフェイス|メソッド|説明
--|--|--
`Consumer<T>`|void accept(T)|引数を受け取って処理をする。結果を戻さない、引数の「消費者」
 `Supplier<T>`|T get()|何も受け取らずに結果だけを戻す「供給者」
 `Predicate<T>`|boolean test(T)|引数を受け取ってそれを評価する「断定」
 `Function<T>`|R apply(T)|引数を受け取って、指定された型（R）の結果を戻す「処理」

## Consumer

Consumerインターフェイスは引数を受け取って消費（処理）する関数を定義するためのもの。

例：Consumer型変数cに、String型の引数を受け取り、その値をHelloという文字列と連結して出力する

```Java
public static void main(String[] args){
  Consumer<String> c = str -> {
   System.out.println("Hello " + str);
  }
  c.accept("Java");
} 
```

## Supplier

Supplierインターフェイスは引数を受け取らず、結果を戻すタイプの関数型インターフェイス。

```Java
public static void main(String[] args){
  Supplier<String> s = () -> {
    return "Hello, Lambda";
  };
  System.out.println(s.get());
}
```

## Predicate

Predicateインターフェイスは、T型の型パラメータをうけとり、そのT型を受け取るtestメソッドにラムダ式を代入する。

例：String型をパラメータとして与えたPredicate型変数を定義し、そのラムダ式を代入している

```Java
public static void main(String[] args){
  Predicate<String> p = str -> {
    return " ".equals(str);
  };
  System.out.println(p.test(args[0]));
}
```

## Function

4つの関数型インターフェイスのうち、ジェネリクス型のパラメータを2つ受け取るのはFunctionだけ。型パラメータの1つ目は引数の型、2つ目は戻り値の型を表す。

```Java
public static void main(String[] args){
  Function<Stirng, Integer> f = str -> {
    return Integer.parseInt(str);
  };
  System.out.println(f.apply("100") * 2);
}
```
