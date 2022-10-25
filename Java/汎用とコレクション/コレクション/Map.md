## Map

基本的な使い方としては、HashMapインスタンスをMap型の変数に格納し、putメソッドを用いてkeyとvalueのセットを追加していく。

```Java
public class Sample{
  public static void main(String[] args){
    Map<Ineger, String> map = new HashMap<>();
    
    map.put(1, "A");
    map.put(2, "B");
    map.put(3, "C");
    
    // keySetでkeyのSetを取り出し、forEachメソッドを用いて、mapのgetメソッドの引数にkeyを順番に入れていく。
    map.keySet().stream().forEach(key -> {
      Sysytem.out.println(map.get(key));
    })
  } 
}
```
出力結果

```console
A
B
C
```

## Map.Entryインターフェース

Map.Entryは、Mapインターフェイス内に定義されたインナーインターフェイスであり、Mapのためだけに利用することを想定したインターフェイス。

キーと値のペアを管理するのが。Map.Entryインターフェース。

```Java
public class Sample{
  public static void main(String[] args){
    Map<String, Integer> map = new HashMapu<>();
    map.put("ONE" ,1);
    map.put("TWO", 2);
    map.put("TREEE", 3);
    
    map.entrySet()
       .stream()
       .forEach((Map.Entry<String, Integer> entry) -> {
        String key = entry.getKey();
        Integer val = entry.getValue();
        System.out.println(key + ":" + val);
       })
  }
}
```

実行結果

```console
ONE:1
TWO:2
THREE:3
```

上記例のように、mapインスタンスを作成後、putメソッドを使用すれば、内部にentryが作られるが、単独でインスタンス化したいのであれば、Mapインターフェイスのentryメソッドを使用する。
このメソッドはstaticなので、インスタンスを生成しなくても利用できる。ただし、このメソッドで作成されたMap.Entryオブジェクトは変更不可能。

また、作ったMap.Entryのインスタンスを使ったMapを作るには、MapインターフェイスのofEntriesメソッドを使用する。このメソッドもstaticであり、インスタンス化の必要はないが、変更不可能なMapを返す。





