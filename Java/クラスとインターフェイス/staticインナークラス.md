## staticインナークラス

ネストされたクラスの中で、staticで修飾したインナークラス。

## Itemクラス内にインナークラスを定義する

Itemクラス内に並び替えの基準を記した、Comparatorインターフェイスを実装したクラスをインナークラスとして定義する。

```Java
package comp;

import java.util.Comparator;


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

  public class PriceComparator implements Comparator<Item> { // インナークラスとして定義
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
}
```

このように実装することで、関係する2つのクラスを1つにまとめ、カプセル化を強化することができる。

## インナークラスのインスタンス化

インナークラスをインスタンス化するには、エンクロージングクラスをインスタンス化した後で、インナークラスをインスタンス化する必要がある。

しかし、上記のItemクラスでは引数に2つの値を渡さないとインスタンス化できないので、何の値を渡せばいいのか？という問題が発生する。下の例のように、意味のないデータを渡すことで無理やりエンクロージング
クラスをインスタンス化することはできるが、推奨されない。

```Java
Collections.sort(items, new Item(null, 0).new PriceComparator());
for(Item item : items){
  System.out.println(item.getName());
}
```

## インナークラスをstaticで修飾する

そこでインナークラスをstaticで定義することにより、エンクロージングクラスのインスタンスを必要としないでstaticインナークラスをインスタンス化することができる。

```Java
public static class PriceComparator implements Comparator<Item> { // staticインナークラスとして定義
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
```

実行クラス

```Java
Collections.sort(items, new PriceComparator()); // エンクロージングクラスのインスタンス化を必要としない
for(Item item : items){
  System.out.println(item.getName());
}

```
