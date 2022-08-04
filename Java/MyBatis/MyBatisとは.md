## MyBatisとは

>MyBatisはSQLとJavaオブジェクトをマッピングするという思想で開発されたDBアクセス用のフレームワーク。MyBatisは、SQLベースでDBアクセスを実現するというレガシーな手法を受け入れつつ、規模が大きめのアプリケーション開発で発生する課題を解決する仕組みを提供している。

**メリット**

* SQLの体系的な管理、宣言的な定義（設定ファイル、アノテーション）
* Javaオブジェクトと、SQL入出力値の透過的なバインディング
* 動的なSQLの組み立て

## SQLの指定方法

* SQLをマッピングファイルに設定（XMLファイルはMapperインターフェイスと同じ階層に配置する）

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN" "http://mybatis.org/dtd/mybatis-3-mapper.dtd" >

<mapper namespace="com.example.demo.repository.HelloRepository">

	<select id="findAll" resultType="com.example.demo.domain.Hello">

		SELECT id, name FROM hello;

	</select>

</mapper>
```

* SQLをアノテーションに指定

```Java
package com.example.demo.repository;


import org.apache.ibatis.annotations.Mapper;
import org.apache.ibatis.annotations.Select;

import com.example.demo.domain.Hello;

@Mapper
public interface HelloRepository {

	@Select("SELECT id, name FROM hello")
	public Hello findAll();

	@Select("SELECT id, name FROM hello WHERE id = #{id}")
	public Hello load(Integer id);
}
```


## 動的SQLについて

MyBatisの応用的な使い方として動的SQLが挙げられる。

**<if>**

**<choose>**

**<foreach>**

**<set>**

**<where>**









