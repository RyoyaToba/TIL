## compare

２つの配列を辞書順に並べた時の並び順を比較する

引数として受け取った２つの配列が等しければ０を戻す

```Java
String[] a = {"apple"};
String[] b = {"apple"};
System.out.println(a,b); // 0
```

第一引数の方が第二引数よりも辞書順で先なら、-1を返す

```Java
String[] a = {"apple"}; // 先
String[] b = {"orange"}; // 後
System.out.println(Arrays.compare(a,b)); // -1
```

第一引数よりも第二引数の方が辞書順で先なら、１を返す

```Java
String[] a = {"orange"}; // 後
String[] b = {"apple"}; // 先
System.out.println(Arrays.compare(a,b)); // 1
```

複数ある場合は、１つ目の要素から判定していきます

```Java
String[] a = {"B", "A"};
String[] b = {"A", "B"};
System.out.println(Arrays.compare(a,b)); // 1
```

```Java
String[] a = {"A", "A"};
String[] b = {"A", "B"};
System.out.println(Arrays.compare(a,b)); // -1
```
