## java.util.Locale

このクラスは、地域や言語といった**ロケール情報**を扱うためのクラス。

```Java
public class Sample {
  public static void main(String[] args){
    Locale locale = Locale.getDefault();
    // 国を表示する
    System.out.println(locale.getCountry());
    // 言語を表示する
    System.out.println(locale.getLanguage());
  }
}
```

Localクラスの**getDefaultメソッド**は、実行しているコンピュータのデフォルトのロケール情報を戻すため、このコードを実行すると、次のように実行しているコンピュータの情報を戻す。

実行結果

```console
JP
ja
```

## ロケールクラスのインスタンス化

ロケールクラスをインスタンス化する方法として、次の5つがある。

* getDefaultメソッドを使う
* コンストラクタを使う
* ロケール変数を使う
* ビルダーを使う
* ファクトリメソッドを使う

Localクラスのコンストラクタは、引数に言語コード、国コード、派生情報の3つを受け取れるよう、オーバーロードされている。

* Locale(String language)
* Locale(String language, String country)
* Locale(String language, String country, String variant)

コンストラクタの第三引数の派生情報は、ベンダーまたはブラウザに固有のコードで、例えば、WindowsにはWIN、MacにはMACなどを使う。もし、派生情報が2つある場合には、それらをアンダースコアで区切り、重要なものを
先に指定する。

Locale locale = new Locale("es", "ES", "Traditional_WIN");




