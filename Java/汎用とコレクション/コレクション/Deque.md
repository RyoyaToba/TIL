## Deque

java.util.Dequeは末尾と先頭の両方から入れて、両方から取り出せるコレクション。double ended queueの省略系であり、デックと発音する。

コード例では、addLastメソッドを使い、末尾からA、Bの順番でキューに入れ、その後、addFirstメソッドを使って、先頭からC、Dの順番でキューに追加している。

```Java
public class Sample{
  public static void main(String[] args){
    
    Deque<String> deque = new ArrayDeque<>();
    deque.addLast("A");
    deque.addLast("B");
    deque.addFirst("C");
    deque.addFirst("D");
    
    deque.stream().forEach(System.out::println);
  }
}

```

取り出す時は、先頭から順番にストリームを使っている。そのため、このコードの実行結果は以下のようになる。

```console
D
C
A
B
```
![図形作成用スライド (4)](https://user-images.githubusercontent.com/105257856/197700337-80fde6f0-3a13-451a-8c49-610ccc0be25e.jpg)
