## Optionalに関して

Java８で新たに追加された　`java.util.Optional`。optionalは値をラップし、その値がnullかもしれないときに使用する。

あるServiceクラスが、idによってhogeEntityを返すfindメソッドがあったとして、その戻り値はnullの可能性が存在すると仮定したとき、

```Java
HogeEntity hogeEntity = service.find(id);

if (hogeEntity != null){
  hogeEntity.getName();
}
```

のように処理を記述するしかない。なぜならば、hogeEntiryがnullの状態で、getName()を呼ぶとそこでエラーが発生するためである。

それを回避するために、Optionalを使用する。

```Java
Optional<HogeEntity> hogeOpt = service.find(id);

hogeOpt.ifPresent(hoge -> hoge.getName()); 
// hogeOptが存在している（nullでない）時のみ、カッコ内のラムダ式を実行する
```
