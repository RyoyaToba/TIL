## CASE：thymeleafでMapを扱う
## ANS: .map.get('hoge').要素で取得できる。

Listの中に、Mapが入っており、それをth:each内で取り出したい場合

例：

`OrderItemList[.../optionMap{'color', 1...}/...]`


```HTML
<span th:each="orderItem : ${orderItemList}>
    <span th:text="${orderItem.item.optionMap.get('color').name}></span>
</span>
```

