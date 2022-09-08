## Spring Boot スキーマ駆動開発を行なってOpenAPIを作成する

参考

Web API開発入門：SpringBootとOpenAPIで始めるスキーマ駆動開発（poco-tech at Udemy）様の動画を視聴しながらまとめ。

![スキーマ駆動開発の全体像](https://github.com/RyoyaToba/TIL/blob/main/documents/openapi-schema-driven1.png)

https://moneyforward.com/engineers_blog/2021/05/28/openapi-schema-driven/


## Spring initializerからプロジェクトを生成する

[Spring initializer](https://start.spring.io/)から条件に合わせてSpring Bootプロジェクトを生成する。今回はgradleを用いてプロジェクトを作成している。


## api-schemaの作成

src/main/resources/内にapi-schema.yamlを作成する。schemaは公式の[リファレンス](https://spec.openapis.org/oas/v3.0.0)を見て作成する。schemaは4.7の部分を参考にする。

```yaml
openapi: '3.0.0'
info:
  title: Library API
  version: '0.0.1'
  description: Library API のドキュメントです
paths:
  /health:
    get: 
      responses:
        '200':
          description: "OK"
```

各項目に関して（公式リファレンスより）

**openapi**

>必須(REQUIRED)。この文字列は、OpenAPI ドキュメントが使用する OpenAPI 仕様書のバージョンのセマンティックバージョン番号でなければなりません (MUST)。openapi フィールドは、ツール仕様とクライアントが OpenAPI ドキュメントを解釈するために使用されるべきです (SHOULD)。これは、API info.version 文字列とは関係ありません。

**info**

>必須。APIに関するメタデータを提供する。メタデータは、必要に応じてツーリングで使用してもよい(MAY)。

**paths**

>必須 APIで利用可能なパスと操作。

## OpenAPI Generator Gradle Pluginを導入する

[OpenAPI Generator](https://github.com/OpenAPITools/openapi-generator)はさまざまな言語とフレームワークに対応したクライアントサイド、サーバーサイドのコードを生成してくれる。

build.gradleにpluginsを記述する。

```gradle
plugins{

}
```
