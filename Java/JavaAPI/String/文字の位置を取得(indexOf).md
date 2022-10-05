## indexOf

StringのindexOfメソッドを使用する

```Java
class Test{
  public static void main(String[] args){
    String text = "あいうえお";
    int target = text.indexOf("あ");
    System.out.print(target); // 0
  }
}
```

もし該当の文字列が存在しない場合は-1を返す。

```Java
class Test{
  public static void main(String[] args){
    String text = "あいうえお";
    int target = text.indexOf("あほ");
    System.out.print(target); // −１
  }
}
```
