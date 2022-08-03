## JPAとは

>JPAは2006年にリリースされたJavaEE５で使用おが定められているJava標準のORM（Object-Relational Mapper）。
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
@Table(name = "hello")
public class Hello {

	@Id
	@Column(name = "id") ・・・（２）
	@GeneratedValue(strategy = GenerationType.IDENTITY)・・・（３）
	private Integer id;

	@Column(name = "name")・・・（２）
	private String name;
  
  //以下ゲッターセッター
	}
}
```

（１）　Entityアノテーションを付与し、Entityクラスであることを宣言
