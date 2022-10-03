## INDEX

* [AWS](#AWS)
* [CSS](#CSS)
* [DataBase](#DataBase)
* [Docker](#Docker)
* [Java](#Java)
* [JavaScript](#JavaScript)
* [Linux](#Linux)
* [OpenAPI](#OpenAPI)
* [Python](#Python)
* [Ruby](#Ruby)
* [SQL](#SQL)
* [cron](#cron)
* [Git](#Git)
* [応用情報](#応用情報)
* [開発](#開発)
* [リファクタリング](#リファクタリング)

## AWS
  - [AWS概要](AWS/AWS概要.md)
  
  - [VPC](AWS/VPC.md)
  
  - [EC2](AWS/EC2.md)
  
  - [Route53](AWS/Route53.md)
  
  - [RDS](AWS/RDS.md)
  
  - [S3](AWS/S3.md)
  
  - [CloudFront](AWS/CloudFront.md)

## CSS

  - bootstrap
       - [grid](CSS/BootStrap/grid.md)
       
       - [form](CSS/BootStrap/Form.md)
       
       - [Card](CSS/BootStrap/Card.md)

## DataBase

  - [正規化](DataBase/正規化.md)

## Docker

  - [Docker基礎](Docker/Docker基礎.md)
  - [Docker Image](https://github.com/RyoyaToba/TIL/blob/main/Docker/Docker%20Image.md)

## Java
 
  - Java API
  
     - Arrays
        
        - [配列のリスト化: asList](https://github.com/RyoyaToba/TIL/blob/main/Java/Java%20API/Arrays/asList.md)
      
        - [辞書順の比較: compare](https://github.com/RyoyaToba/TIL/blob/main/Java/Java%20API/Arrays/compare.md)
        
        - [２つの配列の要素の比較: mismatch](https://github.com/RyoyaToba/TIL/blob/main/Java/Java%20API/Arrays/mismatch.md)
        
     - Character
        
        - [変数の種類判定シリーズ: isAny](https://github.com/RyoyaToba/TIL/blob/main/Java/Java%20API/Character/%E5%A4%89%E6%95%B0%E3%81%AE%E7%A8%AE%E9%A1%9E%E5%88%A4%E5%AE%9A%E3%82%B7%E3%83%AA%E3%83%BC%E3%82%BA.md)
     
     - LocalDate
     
        - [特定の日付を入力する: of](https://github.com/RyoyaToba/TIL/blob/main/Java/Java%20API/LocalDate/of:%20%E7%89%B9%E5%AE%9A%E3%81%AE%E6%97%A5%E4%BB%98%E3%82%92%E5%85%A5%E5%8A%9B%E3%81%99%E3%82%8B.md)
  
     - String
     
        - [文字の位置を取得 : indexOf](https://github.com/RyoyaToba/TIL/blob/main/Java/Java%20API/String/%E6%96%87%E5%AD%97%E3%81%AE%E4%BD%8D%E7%BD%AE%E3%82%92%E5%8F%96%E5%BE%97.md)
        - [文字を抜き出す : substring](https://github.com/RyoyaToba/TIL/blob/main/Java/Java%20API/String/%E6%96%87%E5%AD%97%E3%82%92%E6%8A%9C%E3%81%8D%E5%87%BA%E3%81%99.md)
        - [特定の文字を含んでいるか判定 : contains](https://github.com/RyoyaToba/TIL/blob/main/Java/Java%20API/String/%E7%89%B9%E5%AE%9A%E3%81%AE%E6%96%87%E5%AD%97%E3%82%92%E5%90%AB%E3%82%93%E3%81%A7%E3%81%84%E3%82%8B%E3%81%8B%E5%88%A4%E5%AE%9A.md)
     
     - StringBuilder
     
        - [特定の文字の前に挿入する : insert](https://github.com/RyoyaToba/TIL/blob/main/Java/Java%20API/StringBuilder/%E7%89%B9%E5%AE%9A%E3%81%AE%E6%96%87%E5%AD%97%E3%81%AE%E5%89%8D%E3%81%AB%E6%8C%BF%E5%85%A5%E3%81%99%E3%82%8B.md)
     
     - Stream
     
        - [要素の全件取得：forEach](https://github.com/RyoyaToba/TIL/blob/main/Java/Java%20API/Stream/forEach%EF%BC%9A%E8%A6%81%E7%B4%A0%E3%82%92%E5%85%A8%E4%BB%B6%E8%A1%A8%E7%A4%BA%E3%81%99%E3%82%8B.md)
        - [特定要素の絞り込み：filter](https://github.com/RyoyaToba/TIL/blob/main/Java/Java%20API/Stream/filter%20:%20%E7%89%B9%E5%AE%9A%E8%A6%81%E7%B4%A0%E3%81%AE%E7%B5%9E%E3%82%8A%E8%BE%BC%E3%81%BF.md)
        - [要素を別の要素に変換する：map](https://github.com/RyoyaToba/TIL/blob/main/Java/Java%20API/Stream/map%20:%20%E8%A6%81%E7%B4%A0%E3%82%92%E5%88%A5%E3%81%AE%E8%A6%81%E7%B4%A0%E3%81%AB%E5%A4%89%E6%8F%9B%E3%81%99%E3%82%8B.md)
        - [要素をCollect要素に変換する: collect](https://github.com/RyoyaToba/TIL/blob/main/Java/Java%20API/Stream/collect%20:%20%E8%A6%81%E7%B4%A0%E3%82%92Collect%E8%A6%81%E7%B4%A0%E3%81%AB%E5%A4%89%E6%8F%9B%E3%81%99%E3%82%8B.md)
        - [重複を削除する: distinct](https://github.com/RyoyaToba/TIL/blob/main/Java/Java%20API/Stream/distinct:%20%E8%A6%81%E7%B4%A0%E3%81%AE%E9%87%8D%E8%A4%87%E9%99%A4%E5%8E%BB.md)

        - [要素を並び替える: sorted](https://github.com/RyoyaToba/TIL/blob/main/Java/Java%20API/Stream/sorted:%20%E8%A6%81%E7%B4%A0%E3%82%92%E4%B8%A6%E3%81%B3%E6%9B%BF%E3%81%88%E3%82%8B.md)     
     - List
        
        - [要素の順番を調べる: indexOf](https://github.com/RyoyaToba/TIL/blob/main/Java/Java%20API/List/List.indexOf:%20%E7%89%B9%E5%AE%9A%E8%A6%81%E7%B4%A0%E3%81%AE%E5%A0%B4%E6%89%80%E3%82%92%E8%AA%BF%E3%81%B9%E3%82%8B.md)
        - [要素を直接代入する: of](https://github.com/RyoyaToba/TIL/blob/main/Java/Java%20API/List/List.of:%20%E8%A6%81%E7%B4%A0%E3%82%92%E7%9B%B4%E6%8E%A5%E4%BB%A3%E5%85%A5%E3%81%99%E3%82%8B.md)
        
     - Optional
        - [Optionalとは](https://github.com/RyoyaToba/TIL/blob/main/Java/Java%20API/Optional/Optional%E3%81%A8%E3%81%AF.md)
    
  - Spring   
    
    - Thymeleaf
    
      - [List内のMapの取り出し方](/Java/thymeleaf/List内のmapの取り出し方.md)
      
      - [Selectで引数を渡すには](/Java/thymeleaf/Selectで引数を渡すには.md)
      
      - [th:if_存在しない時は表示させない（エラー回避）](/Java/thymeleaf/存在しない時は表示させない.md)
      
      - [引数を渡すリンク](/Java/thymeleaf/数を渡すリンク.md)
      
      - [td要素にリンクを貼りたい](/Java/thymeleaf/td要素にはリンクは貼れないぞ.md)
      
      - [Formから値を受け取るときのHTML側の書き方](/Java/thymeleaf/Formから値を受け取るときのHTML側の書き方.md)
      
      - [バリデーションチェック](/Java/thymeleaf/バリデーションチェック.md)
    
    - JPA
    
      - [JPAとは](/Java/JPA/JPAとは.md)
    
    - MyBatis
    
      - [MyBatisとは](Java/Spring/MyBatis/MyBatisとは.md)
      
      - [動的SQL](Java/Spring/MyBatis/動的SQL.md)
      
      - [高度なマッピング](Java/Spring/MyBatis/高度なマッピング.md)
    
    - Spring Batch
      
      - [Spring Batch](https://github.com/RyoyaToba/TIL/blob/main/Java/Spring/Spring%20Batch/Spring%20Batch.md)
  
  - DesignPattern
     
     - FactoryMethod
  
  - JUnit
     
     - [Junitの概要](/Java/Junit/Junitの概要.md)
     
     - [Mockito](/Java/Junit/Mockito.md)
     
     - [カバレッジ](/Java/Junit/カバレッジ.md)
     
  - Jsoup
     
     - [Jsoup基本](Java/Jsoup/Jsoup基本.md)
     
     - [NetKeibaスクレイピング](Java/Jsoup/NetKeibaスクレイピング例.md)
  
  - インスタンスとメソッド
  
     - コンストラクタ
     
     - 可変長引数
  
  - 継承
  
     - インターフェイス
     
     - クラスの継承
     
     - 抽象クラス
  
  
  - 配列
  
     - 配列 
  
  - Lombok
    
    - [Lombok](Java/Lombok.md)
  
  - ラムダ式
    
    - [ラムダ式](Java/ラムダ式.md)
   
## JavaScript
  - jQuery
    - [Ajax](/JavaScript/jQuery/Ajax.md)
  
  - [チェックされた値を配列に格納する](/JavaScript/チェックされた値を配列に格納する.md)
  
  - [全てのチェックボックスにイベントを付与する](/JavaScript/全てのcheckboxにイベントを付与する.md)
  
  - [チェックボックスにチェックを入れる](/JavaScript/チェックボックスにチェックを入れる.md) 
  
  - [linear-gradient、四捨五入の仕方](/JavaScript/linear-gradient.md) 
  
  - [特定の数字のBackgroundColorを指定する](/JavaScript/特定の数字にBackgroundColorを設定したい.md)

  - [CORS](/JavaScript/CORS.md)
  
  - [FetchAPI](/JavaScript/FetchAPI.md)
  
## Linux
  - [cat : ファイルの中身を見る](Linux/cat.md)
  
  - [cd : カレントディレクトリの移動](Linux/cd.md)
  
  - [chmod : アクセス権限の変更](Linux/chmod.md)
  
  - [cp : コピー](Linux/cp.md)
  
  - [echo : 書き込み](Linux/echo.md)
  
  - [grep : 検索](Linux/grep.md)
  
  - [less : 中身を見る（全画面表示）](Linux/less.md)
  
  - [ls : ディレクトリ内を調べる](Linux/ls.md)
  
  - [mkdir : ディレクトリの作成](Linux/mkdir.md)
  
  - [mv : ファイルの位置やファイル名の変更](Linux/mv.md)
  
  - [pwd : 現在のディレクトリを調べる](Linux/pwd.md)
  
  - [rm : 削除](Linux/rm.md)
  
  - [tar : ファイルの圧縮や展開](Linux/tar.md)
  
  - [touch : ファイルの作成やタイムスタンプ変更](Linux/touch.md)
  
  - [tail : 最終行から指定した行数だけ表示させる](Linux/tail.md)
  
  - [vi : viエディタを表示してファイルを編集する](Linux/vi.md)
## OpenAPI

  - [APIとは](OpenAPI/APIとは.md)
  
  - [API設計について](OpenAPI/API設計について.md)
  
  - [Spring Bootスキーマ駆動開発](https://github.com/RyoyaToba/TIL/blob/main/OpenAPI/Spring%20Boot%20%E3%82%B9%E3%82%AD%E3%83%BC%E3%83%9E%E9%A7%86%E5%8B%95%E9%96%8B%E7%99%BA.md)

## Python

  - 基本文法

## Ruby

  - 基本文法

## SQL
  
  - [基本構文](/SQL/基本文法.md)
  
  - [集約関数](/SQL/集約関数.md)
  
  - [HAVING](/SQL/HAVING.md)
  
  - [副問合わせ](/SQL/副問合わせ.md)
  
  - [SQLBolt_tutorial](/SQL/SQLBolt_tutorial.md)
  

## cron

  - [cron](/cron/cron.md)

## Git
  - [markdown](/Git/markdown.md)　

## 応用情報

  - [基礎理論](/応用情報技術者試験/基礎理論.md)
  
  - アルゴリズムとプログラミング
  
  - ハードウェアとコンピュータ構成要素
  
  - システム構成要素
  
  - ソフトウェア
  
  - データベース
  
  - [ネットワーク](/応用情報技術者試験/ネットワーク.md)
  
  - [セキュリティ](/応用情報技術者試験/セキュリティ.md)
  
  - システム開発技術
  
  - [マネジメント](/応用情報技術者試験/マネジメント.md)
  
  - ストラテジー

## 開発
  
  - テスト駆動開発
  
  - スキーマ駆動開発

## リファクタリング

  - 関数の切り出し
  
  - 条件の分解
  
  - 条件の統合
  
  - ガード節による置き換え

