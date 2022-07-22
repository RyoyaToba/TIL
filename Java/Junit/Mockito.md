## Mockitoに関して

### 1. Mockitoとは

>Mockitoは、Javaのユニットテストのために開発されたモックフレームワーク（mocking framework）。
モックオブジェクトはテスト対象（テストしたいクラス）から呼び出される依存先のオブジェクトに代わって使用されるテスト用のオブジェクト。

### 2. なぜ、使うのか

```Java

@Service
public class RamService {

  @Autowired
  private RamRepository ramRepository;
	public List<Ram> findAllRams() {
		return ramRepository.findAll();
	}
}
 ```
 上記のクラスをテストしようとする場合、Serviceクラスの成功or不成功は、中で呼び出されている他クラスのメソッドに依存すべきではない。
 ましてや、中で呼び出されるメソッドが未完成の状態でも、該当クラスをテストしたい場合もある。
 そこで、呼び出されるクラスをMockとして置き換えて、テスト対象クラスのみにテストを注力させるためにMockを使用する
 
 ### 3. Mock化の方法について
 
 ```Java
@RunWith(MockitoJUnitRunner.class)
@SpringBootTest
class RamServiceTest {

        @Mock
	private RamRepository ramRepository;

	@InjectMocks
	private RamService ramservice;

	@Test
	void findAllRamsでramRepositoryのfindAllメソッドが呼ばれる() throws Exception {
		ramservice.findAllRams();
		verify(ramRepository, times(1)).findAll();
	}
}
```

Mock対象のクラスに@Mockをつけることで、Mock化することができる。その場合、アノテーションをつけた段階ではMockとして使うことを宣言しているだけになるので実際には使用できない。
そこで初期化処理を行う必要がある。ここでいう初期化とは、Mockオブジェクトを生成することを意味する。
また、MockオブジェクトをつかうことによってMock化することもできる。

Mockオブジェクトを使う場合
```Java
RamRepository ramRepository = mock(RamRepository.class);
```

Mockの初期化
```Java

@RunWith(MockitoJUnitRunner.class)

MockitoAnnotations.init(RamRepository.class);

```

初期化のパターンとしては２種類（？）あり、RunWithアノテーションを付与するか、initメソッドを使うかである。


また、Mockを挿入する方のクラスには@InjectMockをつける。

```Java
@InjectMocks
   private RamService ramservice;
```



