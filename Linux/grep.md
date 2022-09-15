## grep

> grepは検索対象のファイルから文字列を検索するLinuxコマンド
> 正規表現とオプションを使用することで様々な条件で検索が行える。

参考：https://tech-blog.rakus.co.jp/


`grep [option] 検索文字列 対象ファイル`

オプション|説明
--|--
E|拡張正規表現を利用する
e|オプションの引数として検索文字列を指定する
v|結果を反転する。検索文字列を含む行以外を表示
i|検索文字列の大文字と小文字は区別しない
c|マッチした行ではなく、マッチした行数を表示
m[数字]|[数字]行数分だけ表示
B[数字]|マッチした行の前[数字]行を表示
A[数字]|マッチした行の後[数字]行を表示
C[数字]|マッチした行の前後[数字]行を表示
h|出力する行の前にファイル名を付けないようにする
n|頭にそのファイル内での行数を表示

## grep活用例

テスト用のファイルを用意。

```rtf
Yamada
Yamashita
Ishikawa
Tanaka
Sato
Fujita
Kimura
Sakamoto
Ishida
Kawaguchi
Sakashita
```

### 通常の検索

taがつくものを指定

```ターミナル
Yamashita
Fujita
Sakashita
```

大文字小文字は区別されるみたいです。


### AND検索

Fuとtaがつくものを指定

```
grep 'ta' hito.rtf | grep 'Fu'
Fujita
```

### OR検索

拡張正規表現の「|」を使って書く方法か、オプションの「e」を使って書く方法があるようです。

```
grep -e 'ta' -e 'wa' hito.rtf
Yamashita
Ishikawa
Fujita
Kawaguchi
Sakashita
```

```
grep -E 'ta|wa' hito.rtf
Yamashita
Ishikawa
Fujita
Kawaguchi
Sakashita
```

## NOT検索

taを含まないものを検索

```
grep -v 'ta' hito.rtf
Yamada
Ishikawa
Tanaka
Sato
Kimura
Sakamoto
Ishida
Kawaguchi
```

