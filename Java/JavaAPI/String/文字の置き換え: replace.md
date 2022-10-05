## replace

文字の置き換えを行うメソッド。よく使うのは空欄削除など。

```Java
public static void main(String[] args){
  String sample = "Hello World";
  sample = sample.replace(" ", "");
  System.out.println(sample); // HelloWorld
}
```
