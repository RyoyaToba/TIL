## Future

Java SE5 より導入され`java.util.concurrent.Future`インターフェイスは、スレッドを生成したメソッドが、新しく作ったスレッドの結果を知ることができるようになった。

Future型オブジェクトへの参照は、ExecutorServiceやscheduleExecutorServiceにタスクを登録した戻り値として受け取れる。

```Java
public class Sample{
  public static void main(String[] args){
    ExecutorService exec = Executors.newSingleThreadExecutor();
    Future future = exec.submit(() -> {
      try {
        System.out.println("start");
        Thread.sleep(2000);
        System.out.println("end");
      } catch (InterruptedException(e)){
        thorw new RuntimeException(e);
      }
    });
    
    if (future.get() == null){
      System.out.println("finish");
    }
  }
}
```

futureインターフェイスのgetメソッドは、スレッドの処理が終了すれば、nullを返す。

## null以外の値を戻したい場合

null以外の値を戻したい場合、オーバーロードされたsubmitメソッドの第二引数に戻り値を指定する。なお、戻り値の型はFutureの型パラメータによって決まる。

以下の例では、FutureのジェネリクスにString型を設定し、戻り値としてfinishというString型を戻り値として戻す。

```Java
public class Sample{
  public static void main(String[] args){
    ExecutorService exec = Executors.newSingleThreadExecutor();
    Future<String> future = exec.submit(() -> {
      try {
        System.out.println("start");
        Thread.sleep(2000);
        System.out.println("end");
      } catch (InterruptedException(e)){
        throw new RuntimeException(e);
      }
    }, "finish");
    
    String result = future.get();
    System.out.println(result);
  }
}
```



