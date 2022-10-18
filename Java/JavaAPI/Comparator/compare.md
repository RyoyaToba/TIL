## compare

並び替えを行うメソッド。

Itemクラスを定義する。

```Java
package comp;

public class Item implements Comparable<Item> {
  private String name;
  private int price;
  public Item(String name, int price){
    this.name = name;
    this.price = price;
  }
  public String getName(){
    return name;
  }
  public int getPrice(){
    return price;
  }
}
```
値段によって並び替えを行うクラスを定義する。

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

このクラスでは値段を並び替えの基準とし、比較対象となる2つのItemインスタンスのうち、第一引数の方が安ければ-1、高ければ1を、同じであれば0を返すと実装されている。

このように並べ替え対象となるItemクラスから基準を分離することで、並び替えの基準を使用に応じて複数用意することができる。

実行クラスではCollectionsクラスのsortメソッドの第二引数として渡して実行すると、実行結果のように値段順に並び替えられる。

```Java
Collections.sort(items, new PriceComparator());
for (Item item : items){
  System.out.println(item.getName());
}
```

実行結果

```console
banana
orange
apple
```

