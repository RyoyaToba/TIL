## do-while

whileとの違いは判定が処理のあとに行われるという点。そのため、必ず１回は処理が行われる。

```Java
public class Main{

  public static void main(String[] args){
    int a = 0;
    do {
      System.out.println(a++); // 0,1,2,3,4
    } while(a < 5);
  }

}


```

## 参考

Java SE11 Silver 問題集

