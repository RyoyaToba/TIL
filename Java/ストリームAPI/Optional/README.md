## Optional

Java SE8より導入。メソッドの処理結果を扱うクラスであり、処理結果の正常・異常にかかわらず、同じ型で扱うことができる。このクラスを利用することにより、例外処理に関するコードを減らすことができ、可読性が向上する。


## インスタンス生成のためのOptionalクラスのメソッド


メソッド|説明
--|--
static <T> Optional <T> empty()|空のOptionalのインスタンスを生成し、参照を戻す
static <T> Optional <T> of(T value)|null以外の値を持ったOptionalのインスタンスを生成し、参照を戻す
static <T> Optional <T> ofNullable(T value)|値を持っているか、値がnullの場合は、空のOptionalのインスタンスを生成し、参照を戻す
