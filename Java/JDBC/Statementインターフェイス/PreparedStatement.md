## PreparedStatement

## executeUpdateメソッド

データの挿入、更新、削除を行うためのメソッド。実行した結果の件数をint型で戻す。

```Java
public class Main {
  public static void main(String[] args) {
    var sql = "INSERT INTO sample values(?,?)";

    try (Connection con = DBManager.createConnection();
        PreparedStatement pstmt = con.prepareStatement(sql)) {
      pstmt.setInt(1, 1);
      pstmt.setString(2, "jammy");
      pstmt.executeUpdate();
    } catch (Exception e) {
      e.printStackTrace();
    }
  }
}
```

実行結果

```console
+------+-------+
| id   | name  |
+------+-------+
|    1 | jammy |
+------+-------+
```

## executeQueryメソッド

データの検索に使用される。検索結果のテーブルを戻す。

テーブル

```console
+------+--------+
| id   | name   |
+------+--------+
|    1 | jammy  |
|    2 | antony |
+------+--------+
```

```Java
public class Main {

  public static void main(String[] args) {

    var sql = "SELECT * FROM sample";

    try (Connection con = DBManager.createConnection();
        PreparedStatement pstmt = con.prepareStatement(sql)) {
      
      // ResultSetにexecuteQueryメソッドで取得した表を格納する
      ResultSet rs = pstmt.executeQuery();
      
      // nextメソッドにより、行単位で値を指定する
      while (rs.next()) {
        
        // getIntメソッドでは、列番号1(id)を指定している
        System.out.println(rs.getInt(1));
        
        // getStringメソッドでは、カラム名nameの列を指定している
        System.out.println(rs.getString("name"));
      }

    } catch (Exception e) {

      e.printStackTrace();

    }
  }
}
```

実行結果

```console
1
jammy
2
antony
```

## executeメソッド

挿入、更新、削除、検索のいずれも行うことができるメソッド。executeUpdateとexecuteQueryの両方の機能を持つメソッドと解釈できる。

基本的には

SQL文が挿入、更新、削除　 -->  executeUpdate

SQL文が検索 --> executeQuery

SQL文の種類が決まっていない　 -->  execute

このメソッドは、実行結果が、**検索した結果を保持するResultSet型オブジェクト**かどうかをboolean型で戻す。

そのため、戻り値がfalseであった場合は、検索ではなく挿入・更新・削除のいずれかであったことがわかる（ResultSetである表が戻っていない）。

```Java
public class Sample{
  public static void main(String[] args){
    try(Connection con = DBManager.createConnection;){
      
      try (PreparedStatement pstmt = con.prepareStatement(args[0])) {
        
        // もし、executeメソッドの結果がfalseであれば、getUpdateCountメソッドを用いて、結果の件数を取得する
        if (ps.execute() == false){
          System.out.println(ps.getUpdateCount());
          return;
        }
        
        // trueであれば、ResultSetを取り出し
        ResultSet rs = ps.getResultSet();
        
        // メタデータを取得
        ResultSetMetadata meta = rs.getMetaData();
        
        // カラムサイズを取得
        int colSize = meta.getColumnCount();
        while(rs.next()){
          for(int i = 0; i <= colSize(); i++){
            System.out.println(rs.getString(i));
          }
        }
      } catch (Exception e){
        throw new Exception(e);
      }
    }
  }
}
```

上記のように、どちらの場合も使えるメソッドであるが、SQLインジェクションの対策ができないので、実務では使われていない。

## executeBatch

このメソッドは、**1度に複数のSQL文を実行することができる**。

上記3つのメソッドは、1度に1つのSQL文しか実行できなかったので、複数のSQL文を実行したい場合は、逐一呼び出すしかなかった。

```Java
var sql = "INSERT INTO item values(?,?)"
try(PreparedStatement pstmt = con.prepareStatement(sql)){
  
  // 1人目
  pstmt.setInt(1,4);
  pstmt.setString(2, "hoge");
  pstmt.executeUpdate();
  
  // 2人目
  pstmt.set(1,5);
  pstmt.setString(2, "boo");
  pstmt.executeUpdate();
}
```

