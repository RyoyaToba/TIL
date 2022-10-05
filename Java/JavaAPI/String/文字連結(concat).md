## concat

文字の連結に使用するメソッド。stringBuilderクラスにはappendメソッドが存在するので、間違えないように。

```Java
public static void main(String[] args){
  String sample = "abc";
  sample = sample.concat("efg");
  System.out.print(sample); // abcdef
}
```
