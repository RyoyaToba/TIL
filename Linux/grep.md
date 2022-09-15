## grep

> grepは検索対象のファイルから文字列を検索するLinuxコマンド
> 正規表現とオプションを使用することで様々な条件で検索が行える。

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

テスト用のファイルとして、都道府県がローマ字で記述されているファイルを用意する

```txt
Hokkaido
Aomori
Iwate
Miyagi
〜以下略〜
Tottori
Miyazaki
Kagoshima
Okinawa
```

### yamaがつくものを検索

```ターミナル
grep 'yama' todohuken.rtf
Toyama\
Wakayama\
Oakayama\
```

大文字小文字は区別されるみたいです。

### yamaとYamaがつくものを検索（OR検索）

```
grep -e 'yama' -e 'Yama' todohuken.rtf
Yamagata\
Yamanashi\
Toyama\
Wakayama\
Oakayama\
Yamaguchi\
```


参考：https://tech-blog.rakus.co.jp/
