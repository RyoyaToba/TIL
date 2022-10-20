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

