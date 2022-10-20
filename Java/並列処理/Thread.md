## Thread

Threadクラスを継承したサブクラスを定義することで、マルチスレッドを実現する方法に関してまとめ。

以下のように、Threadクラスを継承したサブクラスSampleThreadクラスを定義し、その中でrunメソッドをオーバーライドする。

```Java
public class SampleThread extends Thread {
  @Override
  public void run(){
    System.out.println("sub");
  }
}
```

実行クラスでは、SampleThreadクラスをインスタンス化してThreadクラス型の変数に格納し、startメソッドを実行する。

startメソッドの実行により、新しいスタックが生成され、そこでrunメソッドが実行される。

```Java
public class Main {
  public static void main(String[] args){
    Thread t = new SampleThread();
    t.start();
    
    System.out.println("main");
  }
}
```

mainメソッド内では、mainという文字列を出力するコードも書かれているので、subとmainがコンソール上に出力される。
