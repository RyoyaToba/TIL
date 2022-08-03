## JPAとは

>JPAは2006年にリリースされたJavaEE５で使用が定められているJava標準のORM（Object-Relational Mapper）。
オブジェクト指向言語とDB間の溝を埋めようとする思想。オブジェクトとDBのマッピングを行う役割を担う。

## Entity

DB上の永続化されたデータをマッピングするJavaオブジェクトをEntityと呼ぶ。Entityはメモリ上のJavaオブジェクトのインスタンスで、EntityManagerによりDB上のデータとの同期が行われる。

id|name
--|--
1|hello

上のようなテーブルを作成し、Entityを作成すると、

```Java
package com.example.demo.entity;

@Entity・・・⑴
@Table(name = "hello")・・・（２）
public class Hello {

	@Id・・・（３）
	@Column(name = "id") ・・・（４）
	@GeneratedValue(strategy = GenerationType.IDENTITY)・・・（５）
	private Integer id;

	@Column(name = "name")・・・（４）
	private String name;
  
  //以下ゲッターセッター
	}
}
```

（１）　Entityアノテーションを付与し、Entityクラスであることを宣言

（２）　Tableアノテーションを付与し、マッピングさせるテーブル名を指定する

（３）　Idアノテーションを付与し、主キーであることを宣言する

（４）　Columnアノテーションを付与し、マッピングさせるカラム名を指定する

（５）　GeneratedValueアノテーションを付与することで、主キーの生成をJPAに委ねることができるstrategy属性にGenerateTypeを指定することで、生成方法をしていすることが可能←？
