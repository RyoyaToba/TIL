## do-while

whileとの違いは判定が処理のあとに行われるという点。そのため、必ず１回は処理が行われる。

```Java
public class Main{
  public static void main(String[] args){
    int a = 0;
    do {
      System.out.println(a++); // 0,1,2,3,4
    } while(a < 5);
  }
}
```

## {}の省略

do-whileは{}を省略して記述できる。そのため、上記のコードは以下のように変更が可能。

```Java
public class Main{
  public static void main(String[] args){
    int a = 0;
    do  //{}を省略したもの
      System.out.println(a++); // 0,1,2,3,4
    while(a < 5);
  }
}
```

省略した場合、１行分の記述しかできない。そのため、２行以上の記述を行うとコンパイルエラーになる。

```Java
public class Main{
  public static void main(String[] args){
    int a = 0;
    do
      a++; // コンパイルエラー
      System.out.println(a);
    while(a < 5);
  }
}
```

## 参考

Java SE11 Silver 問題集

