## accumulator

具体的に実行したい処理を記述したBiConsumer型のラムダ式を戻すメソッド。

下記の例では、StringBuilderに、カンマ区切りの文字列を蓄積していく処理を記述している。

このメソッドが戻すBiConsumer型のラムダ式は、処理途中のカンマ区切りの文字列を蓄えるためのStringBuilder型と、ストリーム内の要素であるString型のジェネリクスの型パラメータとして受け取る。

```Java
@Override
public BiConsumer<StringBuilder, String> accumulator() {
  return (builder, str) -> {
    if (builder.length() != 0) {
      builder.append(",");
    }
    builder.append(str);
  }
}
```
