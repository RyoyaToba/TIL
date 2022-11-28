## isEmpty

Optionalの中身がnullかどうか確認するメソッド。空であればtrueを戻し、何か参照が存在すればfalseを戻す。

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
