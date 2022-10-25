## Map

基本的な使い方としては、HashMapインスタンスをMap型の変数に格納し、putメソッドを用いてkeyとvalueのセットを追加していく。

```Java
public class Sample{
  public static void main(String[] args){
    Map<Ineger, String> map = new HashMap<>();
    
    map.put(1, "A");
    map.put(2, "B");
    map.put(3, "C");
    
    // keySetでkeyのSetを取り出し、forEachメソッドを用いて、mapのgetメソッドの引数にkeyを順番に入れていく。
    map.keySet().stream().forEach(key -> {
      Sysytem.out.println(map.get(key));
    })
  } 
}
```
出力結果

```console
A
B
C
```
