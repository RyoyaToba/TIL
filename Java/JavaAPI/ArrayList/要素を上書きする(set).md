## set

setは要素を上書きするメソッド。setメソッドは第一引数に場所、第二引数に要素を指定する。

```Java
ArrayList<String> list = new ArrayList<>();

list.add(0, "A");
System.out.println(list.get(0)); // A

list.set(0, "S");
System.out.println(list.get(0)); // S
```
