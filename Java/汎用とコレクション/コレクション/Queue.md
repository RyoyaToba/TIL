## Queue

java.util.Queueインターフェイスは、FIFOのデータ構造の機能を定義したインターフェイスです。FIFOは、最初に格納した要素を最初に取り出すことのできる仕組みを提供するデータ構造。

```Java
public class Sample{
  public static void main(String[] args){
    Queue<String> queue = new ArrayDeque<>(5);
    queue.add("A");
    queue.add("B");
    queue.add("C");
    queue.add("D");
    queue.add("E");
    
    queue.stream().forEach(System.out::println);
  }
}
```
