## readLine

JavaSE6で導入されたのが、java.io.Consoleクラスであり、コンソールからの入力を受け取る方法を簡略化した。

```Java
public class Sample{
  public static void main(String[] args){
    Console console = System.console();
    String str = console.readLine();
    System.out.println(str);
  }
}
```

readLineメソッドは入力された値を読み込み、String型として戻す。

