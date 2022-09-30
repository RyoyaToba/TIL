## mismatch

異なる配列の要素を比較し、一致しない要素の添字を返すメソッド。

```Java
int[] a = {1,2,3}
int[] b = {1,2,4}
System.out.println(Arrays.mismatch(a,b)); // 2
```

一致しない要素が複数ある場合は、最初の添字を返す

```Java
int[] a = {1,2,3}
int[] b = {1,3,4}
System.out.println(Arrays.mismatch(a,b)); // 1
```

要素数が異なる場合も同じ

```Java
int[] a = {1,2,3}
int[] b = {1}
System.out.println(Arrays.mismatch(a,b)); // 1
```

全てが一致した場合は-1を返す

```Java
int[] a = {1,2,3}
int[] b = {1,2,3}
System.out.println(Arrays.mismatch(a,b)); // -1
```

参考：　Java SE１１　Silver 問題集 p.322開解説
