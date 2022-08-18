**ユーザーの新規登録画面などのように、入力値をFormで受け取る際のthymeleafの書き方**

若干忘れがちなのでメモ。

th:objectとth:fieldの書き方は忘れがち。

```HTML
<form th:action="@{/user/login}" method="post" th:object="${userForm}">
		email:
		<input type="text" name="email" th:field="*{email}"><br />
		password:
		<input type="password" name="password" th:field="*{password}"><br />
		<button>ログイン</button>
		<a th:href="@{/user/register-user}">新規登録</a>
	</form>
```

