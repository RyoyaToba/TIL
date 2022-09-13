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
  id 'org.springframework.boot' version '2.7.3'
  id 'java'
  id 'io.spring.dependency-management' version '1.0.11.RELEASE'
  id 'org.openapi.generator' version "5.3.0"
}
```

## OpenAPI Generator　を使ってスキーマからAPIドキュメントを生成する

[OpenAPI Generator](https://openapi-generator.tech/docs/generators/)

```gradle
task buildApiDoc(type: org.openapitools.generator.gradle.plugin.tasks.GenerateTask){
   generatorName = "html2"
   inputSpec = "$rootDir/src/main/resources/api-schema.yaml".toString()
   outputDir = "$buildDir/apidoc/".toString()
}
```

buildAPIdocを実行すると、APIドキュメントを生成することができる。


## OpenAPI Generatorを使ってスキーマからSpringのコードを生成する

```gradle
task buildSpringServer(type: org.openapitools.generator.gradle.plugin.tasks.GenerateTask){
    generatorName = "spring"
    inputSpec = "$rootDir/src/main/resources/api-schema.yaml".toString()
    outputDir = "$buildDir/spring/".toString()
    apiPackage = "com.example.libraryapi.controller"
    modelPackage = "com.example.libraryapi.model"
    configOptions = [
            interfaceOnly: "true"
    ]
}
```

設定後、スキーマからSpringのコードが自動生成される。

## Gradleタスクの依存関係を設定する

Java compileをした時に、先にSpringコードが自動生成されるように依存関係を設定する。

```gradle
compileJava.dependsOn tasks.buildSpringServer
```

## 生成したコードをインポートできるように設定する

現在の状態では、自動で生成したコードをインポートして利用できない。そのため、gradleに設定を追加する

```gradle
sourceSets.main.java.srcDir "$build/spring/src/main/java"
```

## 起動に必要なライブラリを追加する

```gradle
  implementation 'org.springframework.boot:spring-boot-starter-validation'
  compileOnly 'io.swagger:swagger-codegen-generators:1.6.5'
```

## 全体的な作成の流れ

① スキーマを書く

② スキーマからSpringコード（Interface）を作成する

③　作成したSpringInterfaceのコードをOrverrideし、MVCモデルを実装していく（SpringInterfaceはいじらない）


## クラス構造

![スキーマ駆動開発のシーケンス図](https://user-images.githubusercontent.com/105257856/189841498-e155d99f-88cc-47b5-b66c-f9c7e2b5939f.jpg)

この図が、動画内で紹介されているシーケンス図。最初疑問だったのが、RecordクラスとEntityクラスの必要性である。

この実装を見ると、

① DBから持ってきたデータをRepositoryによって取得し、それをRecordクラスに格納して、Serviceに処理を投げる

② ServiceクラスでRepositoryを呼び出すことで、recordを受け取り、受け取ったrecordをEntityに変換してControllerへ投げる

③　ControllerでServiceを呼び出すことで、Entityを受け取り、受け取ったEntityをDTOに変換してResponceする。

という流れを踏んでいる。これは、recordがDBに依存した関係であり、その他を依存させないための構造になっている。実際、DTOだけで成立する（というか最初そうやって実装していた・・・）が、
DBのデータの変更などに対応するための実装になっているんだと思う。

以下、実際の実装の流れを記述する。途中、かなり勉強になったことがたくさん出てくるので、それはその都度、別ファイルとして保管しておく。

## 大学情報取得APIの作成

### 1. スキーマの記述

エンドポイントは、/university/{id}。

```yaml
paths:
  /university/{id}:　// エンドポイントの記述
    get:
      summary: "大学情報の一件取得" // タイトルのようなもの
      tags: // これを指定しておくと、ドキュメントを見たときにグループ分けされる
        - university
      parameters:
        - name: id // 受け取るパラメータ
          in: path // パラメータの記述場所
          required: true // 必須かどうか
          description: "大学情報を取得するID"
          schema: // 変数の定義
            type: integer 
            format: int64 // long型の指定
      responses:
        '200': // 200レスポンスの時の定義
          description: OK // 返ってくる文字？
          content: // responceBodyの記述
            application/json: // 形式
              schema:
                $ref: "#/components/schemas/UniversityDTO" // 下のcomponentsを指定する
        '404':
          description: NOT FOUND
          content:
            application/json:
              schema:
                $ref: "#/components/schemas/ResourceNotFoundError"

components:　// ResponceBodyを記述する
  schemas:
    UniversityDTO: // 定義して、以下で詳細を記述する
      description: "大学情報を格納したEntityです"
      type: object
      properties:
        id:
          type: integer
          description: "大学ID"
          format: int64
        name:
          type: string
          description: "大学名"
        universityCategoryId:
          type: integer
          format: int32
          description: "大学のカテゴリーを示すID"
        prefectureId:
          type: integer
          format: int32
          description: "都道府県を示すID"
        genderCategoryId:
          type: integer
          format: int32
          description: "共学か女子大かを判別するID"
      required:
        - id
        - name
        - universityCategoryId
        - prefectureId
        - genderCategoryId
    ResourceNotFoundError:
      description: "指定したリソースは存在しない"
      type: object
      properties:
        title:
          type: string
          description: "エラーのタイトル"
          default: "Resource Not Found"
        detail:
          type: string
          description: "エラーの詳細"
      required:
        - title
        - detail
```

定義以後、Springコードを自動生成する。

### 2. Controllerの作成

この時点で、Serviceとかそのほかのクラスは作成していないのでエラーになるが、後々作成してエラーを解消する。

```Java
@RestController // Controllerはviewを返す。RestControllerはJsonやxmlを返す。
@RequiredArgsConstructor　// Lombokを使用している。コンストラクタをDIしてくれるアノテーションと理解している。
public class universityController implements UniversityApi {

    private final UniversityService universityService;  // ここでフィールドとしてServiceを宣言する。

    @Override // 自動生成されたSpringクラスInterfaceをOrverrideする。
    public ResponseEntity<UniversityDTO> universityIdGet(Long id) {
        UniversityEntity universityEntity = universityService.loadById(id); // Entityの取得
        UniversityDTO universityDTO = new UniversityDTO();

        // ここで　Entity -> DTOに詰め替える。
        universityDTO.setId(universityEntity.getId());
        universityDTO.setName(universityEntity.getName());
        universityDTO.setUniversityCategoryId(universityEntity.getUniversityCategoryId());
        universityDTO.setPrefectureId(universityEntity.getPrefectureId());
        universityDTO.setGenderCategoryId(universityEntity.getGenderCategoryId());
        return ResponseEntity.ok(universityDTO); // ResponceEntityにDTOを詰めて返す。
    }
}
```

### 3. Serviceの作成

```Java
@Service
@RequiredArgsConstructor
public class UniversityService {

    private final UniversityMapper universityMapper; // RepositoryのDI
    
    // まず、後述するRepositoryで返されているのはOptional<UniversityRecord>である。
    // Streamによって、recordをEntityに変換している（コンストラクタの呼び出し）
    // orElseThrowとは、おそらく、変換ができなければ後述するエラーを返すようにするメソッドだと思う。
    public UniversityEntity loadById(Long id){
        return universityMapper.loadById(id)
                .map(record -> new UniversityEntity(record.getId(),
                record.getName(),
                record.getUniversityCategoryId(),
                record.getPrefectureId(),
                record.getGenderCategoryId()))
                .orElseThrow(() -> new UniversityEntityNotFoundException(id)); //ここは既存のExceptionを返しても良い。今回は独自のExceptionを作成している。
    }
}
```
Optional<T>に関しては、JavaAPIの方にもまとめておく。　参考　[Optionalとは](https://github.com/RyoyaToba/TIL/blob/main/Java/Java%20API/Optional/Optional%E3%81%A8%E3%81%AF.md)

StreamAPIの方にorElseThrowもまとめておく。

### 4. Repositoryの作成

MyBatisを用いたMapperインターフェイスの実装。今回はアノテーションによるSQLの記述を行なっている。

戻り値はOptional。Idが不正だった場合、検索結果がない。そのため、戻り値をOptionalとしている。

```Java
@Mapper
public interface UniversityMapper {
    @Select("SELECT * FROM university WHERE id = #{id}")
    Optional<UniversityRecord> loadById(Long id);
}
```

### 5. 独自エラークラスの実装

404レスポンスの際、指定したレスポンスを返すように実装する。ここが難しいが、ある程度決まり文句らしいので、記述して見返せばなんとかなりそう。
  
先ほどのServiceクラスの例外処理内で書いた、UniversityEntityNotFoundExceptionを実装する。これはRuntimeExceptionを継承する。
  
  
```Java
public class UniversityEntityNotFoundException extends RuntimeException{

    private Long id; // フィールド変数にidを指定。不正なidがここでキャッチされる。

    // コンストラクタの実装。
    public UniversityEntityNotFoundException(Long id){
        super("id (id = " + id + ") is NOT Found");
        this.id = id;
    }
}
```

上記のクラスが、id不正時に呼び出されるために、ExceptionHandlerを作成する。これが重要。
  
```Java
@RestControllerAdvice // 処理を差し込む
public class CustomExceptionHandler {

    @ExceptionHandler(UniversityEntityNotFoundException.class) //このExceptionが発生したときのハンドラーメソッドであるということ
    public ResponseEntity<ResourceNotFoundError> handleUniversityNotFoundException(UniversityEntityNotFoundException ex){
        var error = new ResourceNotFoundError(); // 呼び出したいErrorインスタンスの生成
        error.setDetail(ex.getMessage()); // Messageをgetする

        return ResponseEntity.status(HttpStatus.NOT_FOUND).body(error);　 // ResponceEntityを呼び出す
    }
}
```
  



  
  
  
  
  
