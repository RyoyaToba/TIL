## Statementインターフェイス

SQLを扱うクラス群として、java.sql.Srarementインターフェイスがある。

SQL文を扱うインターフェイスがPreparedStatement、Statement、DBMSに登録されたストアド・プロージャー（関数）を実行するのに使用されるインターフェイスがCallableStatement。

StatementとPraparedStatementの違いは、パラメータなしのSQL文だけを実行するにはStatementインターフェイスを、パラメータありのSQL文を実行するには、
PreparedStatementインターフェイスを利用する。

基本的にはWHERE句などをつけて実行するのが一般的であるし、SQLインジェクションなどの対策も兼ねて、PreparedStatementを使うのが一般的。
