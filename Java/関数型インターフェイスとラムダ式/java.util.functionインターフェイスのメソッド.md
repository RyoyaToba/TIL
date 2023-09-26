## java.util.functionインターフェイスのメソッド.md

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


