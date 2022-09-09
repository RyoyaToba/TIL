## collect

Streamの要素をListなどに変換するときに使用する。イメージはStreamとしたものを再びListに戻すような感じだと思います。

```Java
Elements elements = document.select("h2.ttl-university");
List<String> nameList = elements.stream() // Streamにする
                        .map(e -> e.String.valueOf(e.text()).replace(" ", "")) //スペースを除去
                        .distinct() //重複除去（詳しくはdistinctへ）
                        .collect(Collectors.toList());　//Stream要素をList要素へ変換
```
