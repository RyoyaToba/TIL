## String

## インスタンス化

Stringクラスのインスタンス化は通常のインスタンス化と異なり、変数名の宣言（と初期化）のみでよく、newによるインスタンス化を必要としない。

```Java
String hoge = "hoge";
```

意図してnewを使ったインスタンス化も可能。

```Java
String hoge = new String();
```

## インスタンスの同一性

同じ参照を指す（同一性：＝＝）に関して、通常のオブジェクトであれば、newをして生成したインスタンスは異なるインスタンスとなるので、変数に格納されているインスタンスの参照は異なる。

```Java
class Item{
  int id;
  String name;
  Item (int id, String name){
    this.id = id;
    this.name = name;
  }
}
```

```Java
Item item1 = new Item(1, "hoge");
Item item2 = new Item(1, "hoge");

// 同じidとnameを持つインスタンスであるが参照が異なる
System.out.println(item1 == item2); // false
```

Stringの場合、同じインスタンス（同じ文字列）を宣言した場合は、コンスタントプールという機能により、同じ文字列は使いまわされるので、同じ参照を指すことになる。
ただし、意図的にnewで宣言した場合には、同じ文字列でも異なる参照のインスタンスを生成することができる。

```Java
String hoge1 = "hoge";
String hoge2 = "hoge";
String hoge3 = new String("hoge");

//　同じ文字列を入れているので参照が同じになる
System.out.println(hoge1 == hoge2); // true

// 意図的にnewを使って宣言
System.out.println(hoge1 == hoge3); // false
```

## immutable

Stringはimmutableな変数である。その変数に変更を加えたとしても、再代入しない限り、それ自体に変更が行われない。

次のコードでは、String型の変数nameを宣言し、Aを代入

その後、replaceメソッドでAをBに変換し

toLowerCaseメソッドにて、小文字に変換している。

感覚的には、bが出力されそうであるが、

```Java
public static void main(String[] args) {
  String name = "A";
  name.replace("A", "B");
  name.toLowerCase();
  System.out.println(name); // A
}
```

出力結果はAのままである。もし結果を反映させたいのであれば、変換した結果を変数に再代入するしかない。

この方法は実現可能であるが、新たにnameというインスタンスを生成することになるので、メモリを無駄に消費することになるので、非推奨である。そのため、StringBuilderなどを使用してそのインスタンス自体
を変更するコードに書き換えるのが良い。

```Java
public static void main(String[] args) {
  String name = "A";
  name = name.replace("A", "B");
  name = name.toLowerCase();
  System.out.println(name); // b
}
```

StringBuiderを用いた変換

```Java
StringBuilder sb = new StringBuilder(name);
sb.replace(sb.indexOf("A"),sb.indexOf("A") +1,"B");
System.out.println(sb); // B
```
