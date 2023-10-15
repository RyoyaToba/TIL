## java.time.format.DateTimeFormatter

このクラスのインスタンスを生成するためには、次の３つの方法がある。

1. 事前に定義された定数を利用する。
2. パターン文字を使用する。
3. ローカライズされたスタイルを利用する。

日付のフォーマットには、ISO8601という国際規格があり、この規則に沿って日付・時刻のフォーマットを行うには、**DateTimeFormatterクラスにあらかじめ定義されている定数**を利用する。

<br>

### 事前に定義された定数

定数|意味|使用例
--|--|--
BASIC_ISO_DATE|基本的なISO日付書式|20111203
ISO_LOCAL_DATE|ローカルのISO日付書式|２０１１-12-03
ISO_LOCAL_TIME|ローカルのISO時刻書式|10:15:30
ISO_ORDINAL_DATE|年および年の日付の書式|2012-337

<br>

### パターン文字

パターン文字は、小文字のa~zと、大文字のA〜Zのアルファベットを使って、日付表記の方法に関する条件を表したもの。
パターン文字を利用してDateTimeFormatterのインスタンスへの参照を取得するには、以下のようにstatcメソッドであるofPatternメソッドを利用する。

```java
DateTimeFormatter.ofPattern("yyyy年mm月dd日")
```

<br>

### ローカライズされたスタイル

フォーマットの指定には、列挙型の`java.time.format.FormatStyle`を利用する。

定数|説明
--|--
FULL|最も詳細なフルテキスト・スタイル
LONG|詳細なテキスト・スタイル
MEDIUM|やや詳細なテキスト・スタイル
SHORT|短いテキスト・スタイル


