## java.util.functionインターフェイスのメソッド.md

<br>

最初に一覧を紹介

<br>

パッケージ|インターフェース|戻り値|メソッド
--|--|--|--
java.util.function|Supplier<T>|T|get()
java.util.function|Consumer<T>|void|accept(T)
java.util.function|BiConsumer<T,U>|void|accept(T,U)
java.util.function|Predicate<T>|boolean|test(T)
java.util.function|BiPredicate<T,U>|boolean|test(T,U)
java.util.function|Function<T,R>|R|apply(T)
java.util.function|BiFunction<T,U,R>|R|apply(T,U)
java.util.function|UnaryOperator<T>|T|apply(T)
java.util.function|BinaryOperator<T>|T|apply(T)
java.lang|Runnable|void|run()
java.util.concurrent|Callable<V>|V|call()


## 何が大事か

- 各インターフェースに定義されているメソッドは暗記する必要あり
  - Supplier(供給者)は、get()
  - Consumer(消費者)は、accept()
  - Predicate(断定)は、test()
  - Function(関数)は、apply()
  - 実務では暗記していたからなんだという感じではあるが、テスト対策としては暗記する必要があり。

- 各インターフェースに定義されているメソッドの引数と戻り値の関係を整理しておく
  - Supplier(供給者)は、引数を受け取らずに戻り値を返す。型はジェネリクス内で指定。
  - Consumer(消費者)は、引数を受け取って、戻り値を返さない。型はジェネリクス内で指定。
  - Predicate(断定)は、引数を受け取って、戻り値を返す。戻り値はboolean。
  - Function(関数)は、引数を受け取って、戻り値を返す。それぞれの型は別々にジェネリクス内で定義可能。

- Functionから派生した系の奴らは、ジェネリクス内の引数の数が違うので整理
  - Function一族は、別々の型を指定可能。Functionは引数と戻り値の２つ、BiFunctionは引数１、引数２、戻り値の３つを指定。
  - なんちゃらオペレーター一族は型が共通。型一緒なのにFunctionで定義する必要なくね？という思想から生まれたと思われる。
