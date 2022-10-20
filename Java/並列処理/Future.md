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

