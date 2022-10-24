## BufferedInputStream

コードが写真データなどを扱う場合、バイトストリームを用いる。次のコードでは、写真データsample.jpgファイルをコピーするコード。

テキストファイルの時と同様で、バッファを用いて効率化を図るのは同じ。

```Java
public class Sample{
  public static void main(String[] args) throws Exception{
    
    // ファイルからバイトストリームを読み込む
    FileInputStream fis = new FileInputStream("Sample.jpg");
    
    // バッファを使って効率化を図る
    BufferedInputStream bis = new BufferedInputStream(fis);
    
    // バイト出力ストリームを使う
    FileOutputStream fos = new FileOutputStream("sample_bk.jpg");
    
    // 入力と同様にバッファを用いて効率化を図る
    BufferedOutputStream bos = new BufferedOutputStream(fos);
    
    try(bis; bos){
      byte[] data = null;
      while((data = bis.readNByte(1024)).length != 0){
        bos.write(data);
      }
      bos.flush();
    }
  }
}
```

バイト入力ストリームでは、BufferedInputStreamが基底クラスのInputStreamクラスから引き継いだreadNBytesメソッドを使って指定した任意のバイト数単位でデータを読み込む。

readAllBytesメソッドで全バイトを1度に取り出すことも可能。

読み込みファイルが終端に達し、さらに読み込むべきバイトが存在しなければ、要素数0のバイト配列が戻されるため、条件式で「0でなければ・・・」を指定する。





