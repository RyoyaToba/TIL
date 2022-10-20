## newFixedThreadPool

あらかじめ決まった数のスレッドを生成し、スレッドプールに貯めておいて使いまわすには、newFixedThreadPoolメソッドを使用する。

```Java
public class Sample{
  public static void main(String[] args){
  
    // 3つのスレッドを作成し、プールしておく
    ExecutorService exec = Executors.newFixedThreadPool(3);
    for(int i = 0; i < 5; i++){
      exec.submit(() -> {
        System.out.println(Thread.currentThread().getId());
      })
    }
  }
}
```

