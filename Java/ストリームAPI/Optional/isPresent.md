## isPresent

Optionalの中身が存在するかどうか確認するメソッド。存在すればtrue、空であればfalseを戻す。

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
