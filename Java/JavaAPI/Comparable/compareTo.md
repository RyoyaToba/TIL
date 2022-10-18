## compareTo

ComparableインターフェイスのcompareToメソッドで、どのように要素を並び替えるかを記述する。

以下の例では、Comparebleインターフェイスを継承したItemクラスを定義し、compareToメソッドをオーバーライドすることで、Itemの順番の並び替えの基準を定義している。

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
  @Override
  public int compareTo(Item item){ // nameによって並び替えることを定義
    return name.compareTo(item.name);
  }
}
```

並び替えを実行するクラスでは、Collectionsクラスのsortメソッドを使って並び替えをしている。実行結果を確認すると、名前順に並び替えられていることが確認できる。

```Java
package conp;

import java.util.Arrays;
import java.util.Collections;
import java.util.List;

public class Main{
  public static void main(String[] args){
    List<Item> items = Arrays.asList(
      new Item[]{
        new Item("orange", 100);
        new Item("banana", 80);
        new Item("apple", 120);
      }
    );
    Collections.sort(items);
    for(Item item : items){
      System.out.println(item.getName());
    }
  }
}
```

実行結果

```console
apple
banana
orange
```



