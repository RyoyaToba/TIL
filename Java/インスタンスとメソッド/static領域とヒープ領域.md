## static領域とヒープ領域

プログラム実行中に必要なクラスをロードして実行するが、ロードされた後、クラスファイルの内容はstaticな領域とそれ以外の領域（ヒープ領域と呼ばれる）に分離され、それぞれ異なるメモリ空間に配置される。

## static領域

ロード後、staticで修飾されたフィールドやメソッドは、「static領域」と呼ばれる領域に排他され、それ以外の部分は「ヒープ領域」と呼ばれる領域に配置される。

![図形作成用スライド (3)](https://user-images.githubusercontent.com/105257856/195253725-8281c7a7-7f1e-4c45-83c4-85b60de1c12f.png)

staticで定義されたフィールドやメソッドはインスタンスを作るための定義とは異なる領域に配置されているため、インスタンスを生成しなくても、staticメンバにはアクセスができる。

## staticなフィールドへのアクセス

```Java
public class sample{
  static int num = 0;
}
```

```Java
public class Main{
  public static void main(String[] args){
    Sample.num = 10; // ①
    Sample s1 = new Sample();
    Sample s2 = new Sample();
    s1.num += 10; // ②
    s2.num = 30; // ③
    System.out.println(Sample.num); // ④
  }
}
```

① staticフィールドへのアクセスは、`クラス名.フィールド名`でアクセスが可能。

② staticフィールドはインスタンスを生成して、`変数名.フィールド名`でもアクセスが可能。その場合でも、numはクラスに属している変数

③ s2からstaticフィールドへアクセスしている。ここで、numの値は30に更新される。

④ num = 30

## それぞれのメンバへのアクセスルール

① staticなメンバからはstaticなメンバしかアクセスできない

② staticでないメンバからはどこへでもアクセス可能（staticでもstaticでなくても）

③ staticなメンバからstaticでないメンバへは、インスタンス経由でならアクセスが可能



## 参考

Java SE11 Silver 問題集
