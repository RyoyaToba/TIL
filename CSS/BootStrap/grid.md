## grid

詳しくは[公式リファレンス](https://getbootstrap.jp/docs/5.0/layout/grid/)を参照。

BootStrapの核と呼んでも良い要素。１列を１２個の要素に分割し、レイアウトを行う。

## 作成した画面

![レース検索 (3)](https://user-images.githubusercontent.com/105257856/190912240-7cc4f2e1-e0d7-4405-8f49-de6024d0b158.png)

個人的に納得は行っていない。。。

## コード

```HTML
<div class="row">
  <div class="raceDay col-3 mt-5 text-center">
    <a href="/horse/race/showRaceList/?&amp;placeNum=6&amp;raceDay=1%E6%9C%885%E6%97%A5(%E7%81%AB)&amp;year=2021">
      <div>1月5日(火)</div>
    </a>
    <div>中山金杯</div>
  </div>
  <div class="raceDay col-3 mt-5 text-center">
    <a href="/horse/race/showRaceList/?&amp;placeNum=6&amp;raceDay=1%E6%9C%889%E6%97%A5(%E5%9C%9F)&amp;year=2021">
      <div>1月9日(土)</div>
    </a>
      <div>ニューイヤーS</div>
  </div>
  <div class="raceDay col-3 mt-5 text-center">
    <a href="/horse/race/showRaceList/?&amp;placeNum=6&amp;raceDay=1%E6%9C%8810%E6%97%A5(%E6%97%A5)&amp;year=2021">
      <div>1月10日(日)</div>
    </a>
      <div>ポルックスS</div>
  </div>
  <div class="raceDay col-3 mt-5 text-center">
    <a href="/horse/race/showRaceList/?&amp;placeNum=6&amp;raceDay=1%E6%9C%8811%E6%97%A5(%E6%9C%88)&amp;year=2021">
      <div>1月11日(月)</div>
    </a>
  <div>フェアリーS</div>
</div>
```

１列にしたい要素を`row`で囲み、子要素に`col-`で範囲を指定する。`col-6`で２分割、`col-4`で３分割。全体が１２。
