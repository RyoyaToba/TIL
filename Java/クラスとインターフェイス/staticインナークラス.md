## staticインナークラス

ネストされたクラスの中で、staticで修飾したインナークラス。

Itemクラス内に並び替えの基準を記した、Comparatorインターフェイスを実装したクラスをインナークラスとして定義する。

```Java





package comp;

import java.util.Comparator;

public class PriceComparator implements Comparator<Item> {
  @Override
  public int compare(Item a, Item b){
    if (a.getPrice() < b.getPrice()){
      return -1;
    }
    if (b.getPrice() < a.getPrice()){
      return 1;
    }
    return 0;
  }
}

```
