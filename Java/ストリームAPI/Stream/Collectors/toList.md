## toList

リストから作成したストリームをフィルタリングして得た結果のみで構成された新しいリストを作成するには、toListメソッドを使用する。

以下のコードでは、フォームによって入力された値のリストから、性別の項目がnullであるものを除き、新しいリストを作成している。

```Java
public List<String> removeNullGenderList(HorseProfileSearchForm form) {
  return form.getGenderList().stream()
                             .filter(e -> e != null)
                             .collect(Collectors.toList());
}
```
