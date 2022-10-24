## readPassword

readPasswordメソッドは、パスワードなどをコンソールに入力させる際に使用され、入力したものがコンソールに表示されなくなる。

```Java
public class UsePassword{
  public static void main(String[] args){
    Console console = System.console();
    char[] password = console.readPassword();
    System.out.println(String.valueOf(password));
  }
}
```

readPasswordメソッドは戻り値としてchar配列型を戻す。
