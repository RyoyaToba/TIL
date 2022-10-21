## get

Optionalからインスタンスを取得するメソッド。getメソッドは、Optionalに参照が入っていることを前提として使用するので、Optionalが空である場合にgetメソッドを呼び出すと、コンパイルエラーが発生する。

コンパイルエラーが発生する例

```Java
public class Sample{
  public static void main(String[] args){
    Optional<String> sample = Optional.empty();
      
      // Optionalが空であるにもかかわらず、getメソッドを使用している
      System.out.println(sample.get());　 
    
  }
}
```

これを回避するためにisPresentメソッドやisEmptyメソッドなどを利用してOptionalの中身を調べる必要がある。

次のコードでは、isPresentメソッドを使用して、Optionalの中身がnullであるので、falseを戻す。

```Java
public class Sample{
  public static void main(String[] args){
    Optional<String> sample = Optional.empty();
    if(sample.isPresent()){
      System.out.println(sample.get()); 
    }
  }
}
```

次のコードは、isEmptyメソッドを利用して、Optionalが空だったときに、trueを返すようにしている。

```Java
public class Sample{
  public static void main(String[] args){
    Optional<String> sample = Optional.empty();
    if(sample.isEmpty()){
      System.out.println("empty");
      return;
    }
    System.out.println(sample.get());
  }
}
```

