## asList

配列からリストのインスタンスを生成するメソッド。作成されたListは固定長となる。

```Java
Integer[] array = {1,2,3};
var list = Arrays.asList(array);
```

もしくは直接インスタンスを代入してもOK

```Java
var list = Arrays.asList(new Integer[] {1,2,3});
```

