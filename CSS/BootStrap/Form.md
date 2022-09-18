## Form

詳しい使い方は[公式リファレンス](https://getbootstrap.jp/docs/5.0/forms/overview/)を参照。

## 作成したフォーム

![新規登録画面](https://user-images.githubusercontent.com/105257856/190911313-c335171b-b435-4993-980f-e1bdec753dd0.png)

## コード

```HTML
<div class="form-group">
  <label for="email">メールアドレス（*必須）</label>
  <input class="form-control" type="text" name="email" th:field="*{email}">
</div>
```

BootStrapを用いたFormレイアウトでは、基本的に`form-group`で１つの入力値を囲う。

入力をしてもらうInput要素には`form-control`クラスを付与し、BootStrapのレイアウトが適用される。


```HTML
<div class="form-row">
  <div class="form-group col-md-6">
    <label for="name">名前（*必須）</label>
     <input class="form-control" type="text" name="name" th:field="*{name}">
  </div>
  <div class="form-group col-md-6">
    <label for="nickname">ニックネーム（*必須）</label>
    <input class="form-control" type="text" name="nickname" th:field="*{nickname}">
  </div>
</div>
```

複数の要素を横並びにする場合は`form-row`タグで囲む。１つ１つのInput要素の大きさはグリッドシステムによって指定する。上記は２つを横に並べた例。

```HTML
<div class="form-row">
  <div class="form-group col-md-3">
    <label for="zipcoad">郵便番号（ハイフンなし）</label>
    <input type="button" class="zipcode-search-btn btn-sm" style="margin-top: -9px;" onClick="zipcoda();" value="住所検索">
    <input class="form-control" type="text" name="zipcode" id="zipcoad">
  </div>
  <div class="form-group col-md-3">
    <label for="prefecture">都道府県</label>
    <input class="form-control" type="text" name="prefecuture" th:field="*{prefecuture}">
  </div>
  <div class="form-group col-md-3">
    <label for="city">市区町村</label>
    <input class="form-control" type="text" name="city" th:field="*{city}">
  </div>
  <div class="form-group col-md-3">
    <label for="cityDetail">丁目番地号アパート名</label>
    <input class="form-control" type="text" name="cityDetail" th:field="*{cityDetail}">
  </div>
</div>
```

こちらが４つの要素を１列に並べた例。


