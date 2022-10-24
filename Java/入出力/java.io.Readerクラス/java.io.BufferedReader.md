## java.io.BufferedReader

java.io.FileReaderクラスの場合は、1文字ずつ読み込むので、100文字あれば、100回繰り返すのでパフォーマンスが低下する。

java.io.BufferedReaderクラスは、文字をバッファに溜め込むことで、何度もネイティブAPIを呼び出さずに、大量の文字を一度に扱える仕組みを提供する。

```Java

public class Sample{
  public static void main(String[] args){
    FileReader fileReader = new FileReader("sample.txt");
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

