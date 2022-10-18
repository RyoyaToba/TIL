## Enum

Enum（列挙型）は、定数をまとめて定義するためのもの。2004年のJava5.0から導入されている。

JavaではEnumはクラスとして定義されており、プログラマが実装したEnumは、java.lang.Enumクラスのサブクラスとして定義され、2つのメソッドが追加される。

Enumの定義

```Java
public enum Fruits{
  APPLE, BANANA, ORANGE, MERON
}
```

自動的に追加されるメソッド

```Java
// 列挙を配列として取り出すメソッド
public T[] values();

// 該当の要素を指定して取り出すメソッド
public T valueOf(String);
```

Enumから要素Aを取り出す

```Java
public enum Test{
  A, B, C
}
```

```Java
public class Main{
  public static void main(String[] args){
    
    // 配列を取り出すメソッドを使用して、その添字の番号を指定
    System.out.println(Test.values()[0]); // A
    
    // 要素を直接指定
    System.out.println(Test.valueOf("A")); // A
  }
}
```

## 



