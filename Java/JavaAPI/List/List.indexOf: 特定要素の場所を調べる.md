## List.indexOf

要素が何番目に存在するか知りたい時、indexOfメソッドを使用する。戻り値はint型。

```Java
List<Integer> numList = List.of(0,1,2,3);

int targetNum = numList.indexOf(2);

System.out.println(targetNum); // 2
```

最初の要素が0番であることに注意すること。
