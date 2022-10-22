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







