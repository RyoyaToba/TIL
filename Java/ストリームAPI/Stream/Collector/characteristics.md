## characteristics

このメソッドは、Collectorの特徴を表すEnumのセットを戻すメソッド。Collectorの特徴には次のような種類があり、Collectorクラスの内部Enumとして、Collector.Characteristicsが用意されている。

列挙子|概要
--|--
CONCURRENT|このCollectorが並行処理をすることを表す
IDENTITY_FINISH|このCollectorのfinisherメソッドが省略可能であることを表す
UNORDERED|コレクションの操作において順序の維持を保証しないことを表す

もし、これらを指定する必要がなければ、次のコードのように`java.util.EnumSetクラス`のnoneOfメソッドにCollector.Characteristicsクラスのクラスリテラルを渡せば、Controller.Characteristcs型を
扱う空のSetオブジェクトが生成される。

```Java
@Override
public Set<Characteristics> characteristics(){
  return EnumSet.noneOf(Characteristics.class);
}
```
