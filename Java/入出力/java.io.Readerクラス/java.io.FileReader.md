## java.io.FileReader

java.io.Readerクラスのサブクラスであり、ファイルを読み込みコンソールに表示するためのもの。

data.txtに以下のことを書き込む。

```txt
hello
java
input
output
stream
```

実行クラス

```Java
public class Sample{
  public static void main(String[] args){
    FileReader reader = null;
    try{
      reader = new FileReader("data.txt");
      int i = 0;
      
      while ((i = reader.read()) != -1){
        char c = (char) i;
        System.out.print(c);
      }
     } finally {
         if (reader != null){
                reader.close();
     }
}     
```

実行結果

```console
hello
java
input
output
stream
```

FileReaderのコンストラクタには、読み込みたいファイルのパスを指定する。コード例では、読み込むテキストファイルである**data.txt**はクラスパス上にあるため、ファイルの名前のみを記述している。

本来であれば、この段階でファイルが存在しなかった場合を想定して検査例外の1つであるcatchブロックが必要になる。

例外が発生せず、ファイルにアクセスできたら、次はファイルの内容を読み込む。ファイル内の文字の読み込みには、Readerクラスから引き継いだreadメソッドを使う。このメソッドは、文字を「コードポイント」という
文字ごとに割り振られている番号で戻すため、読み込みは基本的に1文字単位で行われる。ファイル内のすべての文字を読み込めたら、このメソッドはファイルの終端を表すために-1を戻す。

そのため、コード例のようにint型引数iにreadメソッドの戻り値を代入し、**その値が-1でなければ繰り返し処理を継続する**という条件式のwhile文で先頭の文字から最後の文字までを読み込むことができる。

読み込みが終わり、不要になったストリームは閉じなければいけないので、finnalyブロックでは必ずcloseメソッドを呼び出す。

次のように、try-with-resources文を使うと、リソースの閉じ忘れを防止できる。

```Java
public class Sample{
  public static void main(String[] args){
    FileReader reader = null;
    try(reader){
      reader = new FileReader("data.txt");
      int i = 0;
      
      while ((i = reader.read()) != -1){
        char c = (char) i;
        System.out.print(c);
      }
    }
}     
```




