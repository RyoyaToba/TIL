## java.io.BufferedReader

java.io.FileReaderクラスの場合は、1文字ずつ読み込むので、100文字あれば、100回繰り返すのでパフォーマンスが低下する。

java.io.BufferedReaderクラスは、文字をバッファに溜め込むことで、何度もネイティブAPIを呼び出さずに、大量の文字を一度に扱える仕組みを提供する。

```Java

public class Sample{
  public static void main(String[] args){
    FileReader fileReader = new FileReader("data.txt");
    BufferedReader reader = new BufferedReader(fileReader);
    try(reader){
      String line = null;
      while((line = reader.readLine()) != null){
        System.out.println(line);
      }
    }
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
StreamAPIを使えば、BufferedReaderでの読み込みは簡潔に記述できる。次のコードが、StreamAPIで修正したものになる。

```Java
public class Sample{
  public static void main(String[] args){
    FileReader fileReader = new FileReader("data.txt");
    BufferedReader reader = new BufferedReader(fileReader);
    try(reader){
      reader.lines().forEach(System.out::println);
    }
  }
}
```





