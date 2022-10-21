## combiner

このメソッドの目的は、並列処理をしているときに、個々に作られた処理途中の値を保持するためのオブジェクトを結合すること。

ここでは、2つのStringBuilderを受け取り、結合する処理をcombinerメソッドに実装する。なお、combinerメソッドの戻り値型は、結合対象であるオブジェクト2つを引数として受け取るBinaryOperator型である。

```Java
public BinaryOperator<StringBuilder> combiner() {
  return (a, b) -> {
    a.append(",");
  }
  a.append(b);
  return a;
}
```
