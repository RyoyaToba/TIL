## finisher

処理結果を戻すラムダ式を提供するメソッド。

```Java
@Override
public Function<StringBuilder, String> finisher(){
  return builder -> builder.toString();
}
```
