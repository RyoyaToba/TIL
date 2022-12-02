## ControllerTest

Controllerのテストを行う際の基本的な使い方をまとめる。

## セットアップ

MockMvcを使えるようにするには、２つどちらかのセットアップを行う必要がある。テストを行う際は、それぞれの特徴を把握し、用途ごとに適したオプションを参照すること。

動作オプション|概要
--|--
webAppContextSetup|spring-mvc.xmlなどで定義したSpringMVCの設定を読み、webApplicationContextを生成することで、デプロイ時とほぼ同じ状態でテストすることができる
standaloneSetup|ControllerにDIされているコンポーネントを、テストで利用する設定ファイルに定義することで、SpringTestが生成したDIコンテナを用いてテストを行うことができる。よって、SpringMVCのフレームワーク機能を利用しつつ、Controllerのテストを単体テスト観点で行うことができる。

コード例

```Java
private MockMvc mockMvc;

@Autowired
WebApplicationContext wac;

@Autowired
private ObjectMapper mapper;

@InjectMocks
private SettingQuestionnaireController controller;

@MockBean
private SettingQuestionnaireService service;

@BeforeEach
void setUp() throws Exception {
	MockitoAnnotations.openMocks(this);
  // mockMvcのセットアップ
	mockMvc = MockMvcBuilders.standaloneSetup(controller).build();
  // springSecurityを適応させる
	mockMvc = MockMvcBuilders.webAppContextSetup(wac).build();
}
```

## 参考

