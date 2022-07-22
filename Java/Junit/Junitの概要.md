## Junitに関するまとめ

### 第６章　テストの構造化

テストコードもプロダクションコードと同様に、可読性が高くなるようにメンテナンスをするべき。可読性が高いテストコードとは何かを探っていく。

- テストコードの初期化処理は似たようなコードが多くなる
- Beforeアノテーションで定義する共通の処理は１つが望ましい　→ 実行順序が制御できず、すべて実行されるため
- テストケースが増えてきたら、なんらかの基準でグループ化し、テストクラスを構造化するべき

#### 初期処理を共通化したいので、テストケースは[共通の初期処理]でグループ化をするべき

```Java

@RanWith(Enclosed.class)
public class ItemStockTest{
  public static class 空の場合{
    ItemStock sut;
    
    @Before
    public void setUp() trows Exception(){
      sut = new ItemStockImpl();
    }
    
    @Test
    public void size_Aが0を返す() throws exception {
      assertThat(sut.size("A")), is(0));
    }

    @Test
    public void contains_Aはfalseを返す() throws Exception{
      assertThat(sut.contains("A"), is(false));
    }
 }
    public static class 商品Aを1件含む場合{
    ItemStock sut;
    
    @Before
    public void setUp() trows Exception(){
      sut = new ItemStockImpl();
      sut.add("A", 1);
    }
    
    @Test
    public void size_Aが1を返す() throws exception {
      assertThat(sut.size("A")), is(1));
    }

    @Test
    public void contains_Aはtrueを返す() throws Exception{
      assertThat(sut.contains("A"), is(true));
    }
 }   
}
```


