## Collector

`java.util.stream.Collector`インターフェイスは、3つの型パラメータを受け取る。

1つ目がストリーム内の要素の型

2つ目が処理途中の値を保持するためのオブジェクト

3つ目が最終的な結果の型

Collectorには、[`supplier`](supplier.md)、[`accumulator`](accumulator.md)、[`combiner`](combiner.md)、[`finisher`](finisher.md)、[`characteristics`](characteristics.md)という5つの抽象メソッドがあり、これら全てを実装しなければならない。
