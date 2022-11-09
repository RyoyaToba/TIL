## HTMLを挿入する

ユーザーのボタン操作により、表示しているHTMLの内容を差し替える方法

```HTML
<main class="mdl-layout__content mdl-color--grey-100">
            <div class="btn_set">
                <button>アンケート作成</button>
                <button>結果表示</button>
                <button>回答募集アンケート変更</button>
                <button id="admin-edit-btn" value="edit" onclick="editClick()">管理者情報変更</button>
            </div>
            <!--DOM操作によるテキスト挿入部分-->
            <div id="insert-text"></div>
        </main>
```

４つのボタンを用意し、それぞれのボタン操作によって、表示内容を切り替える。管理者情報変更ボタンにはonclick属性でeditClickFunctionを指定。

```Javascript
// ボタンの取得
let adminEditBtn = document.getElementById('admin-edit-btn');
// 差し込む部分の取得
let insertText = document.getElementById('insert-text');

// ボタンを押したときの関数
function editClick(){
    insertText.innerHTML = editAdminText;
}

// 差し込む内容
const editAdminText = '<div style="margin:10px 10px">' 
               + '<form th:action="@{/admin/register/do}" id="regist-form" th:object="${administratorForm}" method="post">'
                   + '管理者名：<span th:errors="*{name}" style="color:red"></span><br />'
                   + '<input type="text" name="name" th:field="*{name}"><br />'
                   + 'メールアドレス：<span th:errors="*{email}" style="color:red"></span><br />'
                   + '<input type="text" name="email" th:field="*{email}"><br />'
                   + 'パスワード：<span th:errors="*{password}" style="color:red"></span><br />'
                   + '<input type="password" name="password" th:field="*{password}"><br />'
                   + '<input type="submit" id="regist-btn" value="登録" style="margin-top:10px">'
              + '</form>'
           + '</div>';
```

innerHTMLでは要素の上書きになる。

<img width="1440" alt="スクリーンショット 2022-11-09 11 10 34" src="https://user-images.githubusercontent.com/105257856/200727939-ac671f94-0a60-4a5c-a166-25528f0a22a1.png">


