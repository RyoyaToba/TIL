## scheduleメソッド

遅延実行する方法はScheduedExecutorServiceのscheduleメソッドを使用する。このメソッドは3つの引数を受け取る。

**第一引数**

`java.util.Runnable`型の実行したい処理

**第二引数**

long型の遅延させる時間

**第三引数**

遅延させる時間の単位（`java.util.concurrent.TimeUnit`列挙型）

この列挙型には24時間を表すDAYS、1時間を表すHOURS、1分を表すMINUTES、1秒を表すSECONDS喉の列挙定数が定義されており、第二引数と合わせて、遅延させる時間を表現する。

```Java
public class Sample{
  public static void main(String[] args){
    ScheduledExecutorService exec = Executors.newSingleThreadScheduledExecutor();
    exec.schedule(() -> {
      System.out.println("finish");
      exec.shutdown();
    }, 1, TimeUnit.SECONDS);
    
    int count = 0;
    while (true){
      Thread.sleep(100);
      if(exec.isShutdown()){
        break;
      }
      System.out.println((++count) * 100 + " ms");
    }
  }
}
```

実行結果。

```console
100 ms
200 ms
300 ms
// 省略
800 ms
900 ms
finish
```




