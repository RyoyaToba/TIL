## List.of

いつも　`new ArrayList<>()`を使っていたので、直接代入するのが不思議だったので、備忘録として。

```Java
List<Integer> numList = List.of(0,1,2);
```

この場合、作成された配列は固定長（大きさが変えられない）となる。そのため、addやremoveで長さの変更を行おうとすると、例外がスローされる。

```Java
List<Integer> numList = List.of(0,1,2);
list.add(9); // UnsupportedOperationException
```

```Java
List<Integer> numList = List.of(0,1,2);
list.remove(0); // UnsupportedOperationException
```

あまり使う場面はないかも。
