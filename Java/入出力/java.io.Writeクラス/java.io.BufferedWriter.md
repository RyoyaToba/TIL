## java.io.BufferedWriter

FileReaderクラスが1文字ずつ読み込むのと同様に、FileWriterクラスも1文字ずつ処理を行うので、文字数が多くなるとパフォーマンスが低下する。

このため、文字出力ストリームにもバッファを利用するクラスとして、java.io.BufferedWriterが用意されている。

```Java
public class Sample{
  public static void main(String[] args){
    FileWriter out = new FileWriter("output.txt", true);
    BufferedWriter writer = new BufferWriter(out);
    try(writer){
    
      // 改行コードを出力するための専用のメソッド
      writer.newLine(); 
      
      // ファイルに直接書き込むのではなく、バッファに書き込む。
      writer.write("Buffering output"); 
      
      // flushメソッドによってバッファとファイルを同期させる
      writer.flush(); 
    }
  }
}
```


