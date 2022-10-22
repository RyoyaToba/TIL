## java.io.FileReader

java.io.Readerクラスのサブクラスであり、ファイルを読み込みコンソールに表示するためのもの。

```Java
public class Sample{
  public static void main(String[] args){
    FileReader reader = null;
    try{
      reader = new FileReader("sample.txt");
      int i = 0;
      
      while ((i = reader.read()) != -1){
        char c = (char) i;
        System.out.println(c);
      }
     } finally {
         if (reader != null){
                reader.close();
     }
}     
```

FileReaderのコンストラクタには、読み込みたいファイルのパスを指定する。コード例では、読み込むテキストファイルである「sample.txt」はクラスパス上にあるため、ファイルの名前のみを記述している。
本来であれば、この段階でファイルが存在しなかった場合を想定して検査例外の1つであるcatchブロックが必要になる。







