## scheduleAtFixedRate

scheduleメソッドは、処理を１回だけ遅延実行するメソッドだったが、ScheduledExecutorServiceが終了するまで定期的に繰り返し実行するためには、このメソッドを用いる。

このメソッドでは、初期の遅延時間と２回目以降のインターバル時間の２つを指定する。

```java
exec.sheduleAtFixedRate(() -> {
  System.out.println("hoge");
},1, 1, TimeUnit.SECONDS) ;
```

