## newSingleThreadExecutor

Executorsクラスに存在するnewSingleExecutorメソッドは、別のタスクを持つ新しいスレッドを1つだけ作ってプールしている、ExecutorServiceを生成する。

```Java
public class Sample{
  public static void main(String[] args){
    
    // スレッドの生成
    ExecutorService exec = Executors.newSingleThreadExecutor();
    
    // for文を使って、スレッドにタスクを与えて実行するsubmitメソッドを5回呼び出している
    for (int i = 0; i < 5; i++){
      exec.submit(() -> {
        System.out.println(Thread.currentThread().getId()); // スレッドのIDを取得
      });
    }
  }
}
```

