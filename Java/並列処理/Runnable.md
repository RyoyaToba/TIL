## Runnable

Javaにおいて、Runnableインターフェイスを実現したクラスを用意し、そのインスタンスをThreadクラスのコンストラクタに渡す方法についてまとめ。

Runnableインターフェイスは、新しいスレッドで実現したい処理を記述するためのrunメソッドのみを持っている。

```Java
public class Sample{
  public static void main(String[] args){
    Thread t = new Thread(new Runnable(){ // Runnableインターフェイスを実現した匿名クラスを定義している
      @Override
      public void run(){
        System.out.println("sub");
      }
    });
    t.start();
    System.out.println("main");
  }
}
```

記述している内容は、[Threadクラスのサブクラスを定義する方法](Thread.md)と変わらないので、比較をしてみるといい。

また、Runnableインターフェイスは、関数型インターフェイスなので、ラムダ式で書き替えることが可能であり、そちらの方が記述量が少なく可読性も増す。

```Java
public class Sample{
  public static void main(String[] args){
    Thread t = new Thread( () -> {
        System.out.println("sub");
    });
    t.start();
    System.out.println("main");
  }
}
```
