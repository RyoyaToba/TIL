## PreparedStatement

**executeUpdateメソッド**は、データの挿入、更新、削除を行うためのメソッド

```Java
var sql = "insert into item values(?,?)";
try(PreparedStatement pstmt = con.preparedStatement(sql)){
  pstmt.setInt(1,2);
  pstmt.setString(2, "sample");
  pstmt.executeUpdate();
}
```

executeQuery

execute

executeBatch

