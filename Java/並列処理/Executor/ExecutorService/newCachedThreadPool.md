## newCachedThreadPool

固定数のスレッドではなく、必要に応じてスレッドを増減させるスレッドプールを作るには、newCatchedThreadPoolメソッドを使う。一度生成されたスレッドは60秒間使用されなければ破棄され、
60秒未満であれば再利用されるため、無駄がない。

```Java
public class Sample{
  public static void main(String[] args) throws Exception{
    ExecutorService exec = Executors.newCachedThreadPool();
    Runnable test = () -> {
      System.out.println(Thread.currentThread().getId());
    };
    
    for (int i = 0; i < 5; i++){
      exec.submit(test);
    }
    
    Thread.sleep(1 * 10000);
    System.out.println("-----10秒後-----")
    
    for (int i = 0; i < 5; i++){
      exec.submit(test);
    }
    
    Thread.sleep(1 * 70000);
    System.out.println("-----70秒後-----")
    
    for (int i = 0; i < 5; i++){
      exec.submit(test);
    }
  }
}
```

実行結果

```console
13
12
14
15
12
-----10秒後-----
// 10秒しかたっていないのでスレッドは使いまわされる
15
14
12
13
15
-----70秒後-----
// 60秒以上たっているので、スレッドプール内のスレッドが破棄され、新しいスレッドが生成されている
17
17
18
19
20
```
