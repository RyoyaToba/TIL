## remove

要素を削除するにはremoveを使用する。このメソッドはオーバーロードされており

➀ 配列の番号を指定して削除する

```Java
ArrayList<String> list = new ArrayList<>();
list.add("A");
list.add("B");
list.add("C");
list.add("D");

list.remove(1); // Bが削除される
```

➁ オブジェクトを指定して同値判定で削除する

Itemクラスの定義

```Java
public class Item{
  private String name;
  private int price;
  public Item(String name, int price){
    this.name = name;
    this.price = price;
  }
  
  // equalsメソッドのオーバーライド
  public boolean equals(Object obj){
    if (obj instanceof Item){
      Item tmp = (Item) obj;
      if (tmp.name.equals(this.name)){
        return true;
      }
      return false;
    }
   public String getName(){
    return name;
   } 
}
```

Mainクラスの実装

```Java

```
