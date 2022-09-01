## Lombokとは

> Lombok は、 Java言語におけるボイラープレートコードをソースコードから排除するために使用するライブラリである。
> ボイラープレートコードとは、言語仕様上省く事ができない定型的なコードの事である。 ボイラープレートコードは本質的なロジックでないため、アプリケーションを実装する上で冗長なコードとなる。
> Java言語における代表的なボイラープレートコードには、
> メンバー変数にアクセスするための getter / setter メソッド
> equals/hashCodeメソッド
> toStringメソッド
> コンストラクタ
> リソース(入出力ストリーム等)のクローズ処理
> ロガーインスタンスの生成
> 等がある。
> Lombokは、これらのボイラープレートコードをコンパイル時に生成することで、 開発者が実装するソースコード上から冗長なコードを取り除く仕組みを提供している。

[参考](https://terasolunaorg.github.io/guideline/5.0.0.RELEASE/ja/Appendix/Lombok.html#:~:text=Lombok%20%E3%81%AF%E3%80%81%20Java%E8%A8%80%E8%AA%9E%E3%81%AB%E3%81%8A%E3%81%91%E3%82%8B,%E5%86%97%E9%95%B7%E3%81%AA%E3%82%B3%E3%83%BC%E3%83%89%E3%81%A8%E3%81%AA%E3%82%8B%E3%80%82)

Lombok使用前

```Java
public class sampleDTO {
  private String content;
  private LocalDateTime timestamp;
  
  // コンストラクタ
  public SampleDTO(String content, LocalDatetime timestamp){
    this.content = content;
    this.timestamp = timestamp;
  }
  
  //以下ゲッター
  public String getContent{
    return content;
  }
  
  public LocalDateTime getTimestamp(){
    return timestamp;
  }

}
```

Lombok使用後

```Java
@Value // このアノテーションをつけることでコンストラクタやゲッターが自動生成される
public class sampleDTO {
    String content;
    LocalDateTime timestamp;
}
```
