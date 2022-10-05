## distinct

Collect要素や配列に重複する要素を取り除くための操作

```Java
Elements elements = document.select("h2.ttl-university");
List<String> nameList = elements.stream() // Streamにする
                        .map(e -> e.String.valueOf(e.text()).replace(" ", "")) //スペースを除去
                        .distinct() //重複除去（詳しくはdistinctへ）
                        .collect(Collectors.toList());　//Stream要素をList要素へ変換
```

distinct操作前は、List内の要素には[〇〇大学, 〇〇大学]と言う風に同じ要素が２つ存在する。そのため、distinctを中間操作に加えることで、重複を解消している。
