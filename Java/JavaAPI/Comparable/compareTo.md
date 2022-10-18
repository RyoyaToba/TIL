## compareTo

ComparableインターフェイスのcompareToメソッドで、どのように要素を並び替えるかを記述する。以下の例では、Comparebleインターフェイスを継承したItemクラスを定義し、compareToメソッドをオーバーライドする
ことで、Itemの順番の並び替えの基準を定義している。

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



