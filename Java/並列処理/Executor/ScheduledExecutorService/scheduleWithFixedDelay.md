## scheduleWithFixedDelay

scheduleAtFixedRateメソッドでは、前の処理と次の処理までのインターバルの両方が終了していれば、以降の処理が実行される。
そのため、インターバルが終了するまで次の処理が開始を待たなくてはいけない場合もあり、次の処理と次の処理の間隔が一定でない。

もし、処理の長さに管毛なく、インターバルを一定にしたいのであれば、scheduledWithFixedDelayメソッドを利用する。

このメソッドでは、繰り返したい処理と、初期遅延、インターバルを指定する。

```java
exec.scheduleWithFixedDelay(() -> {
  int r = new Ramdom().nextInt();
  System.out.print(r);
  try {
    Thread.sleep(r * 100);
  } catch(InterruptedExecution e) {
      System.out.println(e.getMessage());
  }
  System.out.println("interrupt");
}, 1, 1, TimeUnit.SECONDS);
```
