## CallableStatement

## ストアド・プロシージャ

SQL文や専用の言語を組み合わせて処理手順を記述し、DBに保存したもの。ストアド・プロシージャでは、条件分岐やループといった制御構文、変数、例外処理など、一般のコンピュータプログラムとかわらない高度な機能を
利用できる。

ストアド・プロシージャを記述するには、各DBMS独自の言語を用いるのが一般的であり、これらは便利な反面、完全な互換性があるわけではないので特定のDBMS製品に固定されてしまい、変更に弱くなるという弱点がある。

なお、Apache DerbyはJavaで作られていることもあり、Javaのプログラムをストアド・プロシージャとして登録することができる。

作成したクラスをjarファイルとしてまとめ、Derbyのコマンドラインクライアントを起動し、jarファイルを登録し、ストアド・プロシージャを作成する。


以下のコードのように、ストアド・プロシージャを呼び出すコードを作成する。

```Java
public class CallSample{
  public static void main(String[] args){
    try(Connection con = DBManager.createConnection()){
      
      // プロシージャの取得 
      String proc = "CALL UPDATE_ITEM(?,?)";
      
      // 引数にプロシージャ名を渡す
      try(CallableStatement cs = con.prepareCall(proc)){
        cs.setString(1, "call procedure");
        cs.setInt(2,1);
        cs.execute();
      }
    } cathch (Excption e){
      throw new Exception(e);
    }
  }
}
```

ストアド・プロシージャを呼び出すには、`java.sql.CallableStatement`インターフェイスを使う。CallableStatement型のオブジェクトは、prepareCallメソッドに、呼び出すストアド・プロシージャ名を
渡して取得する。


