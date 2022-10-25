## PreparedStatement

**executeUpdateメソッド**は、データの挿入、更新、削除を行うためのメソッド。実行した結果の件数をint型で戻す。

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

**executeQuery**メソッドは、データの検索に使用される。検索結果のテーブルを戻す。

```Java




```

execute

executeBatch

