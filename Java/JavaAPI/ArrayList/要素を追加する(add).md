## add

要素を追加するにはaddメソッドを使用する

オブジェクトであれば、どんな型の集合でも扱える。

```Java
public static void main(String[] args){
    ArrayList list = new ArrayList();
    list.add(new Object);
    list.add("test");
    list.add(new Integer(10));
}
```

## ジェネリクス

基本的には、バグの温床となるのを避けるために、Java SE 5から導入されたジェネリクスを用いて型指定を行う。これによって代入できる型を制限することで、
思わぬバグを生まない。


ジェネリクスによる型宣言をしない場合、要素は自動的にObject型であると認識される。

```Java
ArrayList<String> list = new ArrayList<String>();
```

また、Java SE 7 からダイヤモンド演算子が導入されたことで、ジェネリクスを簡潔に記述できるようになった。

```Java
ArrayList<String> list = new ArrayList<>();
```

