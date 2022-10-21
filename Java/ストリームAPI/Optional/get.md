## get

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

