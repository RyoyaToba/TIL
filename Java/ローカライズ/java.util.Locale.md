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

### コンストラクタ

Localクラスのコンストラクタは、引数に言語コード、国コード、派生情報の3つを受け取れるよう、オーバーロードされている。

* Locale(String language)
* Locale(String language, String country)
* Locale(String language, String country, String variant)

コンストラクタの第三引数の派生情報は、ベンダーまたはブラウザに固有のコードで、例えば、WindowsにはWIN、MacにはMACなどを使う。もし、派生情報が2つある場合には、それらをアンダースコアで区切り、重要なものを
先に指定する。

Locale locale = new Locale("es", "ES", "Traditional_WIN");

### ロケール変数

コンストラクタの場合、不正な値を設定してインスタンス化してもコンパイルエラーにならない。また、コンパイル後も例外がスローされることもない。

例

```Java
Locale locale = new Locale("aa", 22);
```

その結果、言語コードや国コードに間違いがあっても気がつかないという問題が発生する。そこでそのような間違いを起こさないようにするために、次のような**ロケール変数**が用意されている。

定数|言語|国|説明
--|--|--|--
static Locale.JAPAN|ja|JP|日本のロケール情報
static Locale.US|us|US|アメリカのロケール情報
static Locale.CANADA|en|CA|カナダのロケール情報
static Locale.CANADA_FRANCH|fr|FR|カナダのロケール情報
static Locale.UK|en|GB|イギリスのロケール情報

次のようにロケール変数を使用することで、言語コードや国コードの間違いを防ぐことができる。

```Java
Locale locale = Locale.CANADA_FRENCH;
```

### ビルダー

ビルダーとは、インスタンスを組み立てるクラスのこと。

JavaSE7以降では、さらに詳細な情報を扱えるようにインターネット技打つの標準化団体「IETF」が定めるIETF言語タグに対応するようになった。そのIETF言語タグでは、細かなロケール情報を表現するために、
次のような情報（下位タグ）の組み合わせで構成されており、これらをハイフンで区切って1つの文字列として表す。

* language(言語)
* script(文字体系)
* region(地域)
* variant(派生)
* extension(拡張)
* privateuse(私用)

ロケール情報をIETF言語タグで表現するには、次のコード例のようにLocaleクラスのインスタンスを生成し、そのインスタンスの`toLanguageTagメソッド`を使用する。

```Java
Locale locale = new Locale("ja", "JP", "JP");
System.out.println(locale.toLanguageTag());
```




