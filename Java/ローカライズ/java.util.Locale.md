## java.util.Locale

このクラスは、地域や言語といった**ロケール情報**を扱うためのクラス。

```Java
public class Sample {
  public static void main(String[] args){
    Local local = Local.getDefault();
    // 国を表示する
    System.out.println(local.getCountry());
    // 言語を表示する
    System.out.println(local.getLanguage());
  }
}
```

Localクラスの**getDefaultメソッド**は、実行しているコンピュータのデフォルトのロケール情報を戻すため、このコードを実行すると、次のように実行しているコンピュータの情報を戻す。

実行結果

```console
JP
ja
```


