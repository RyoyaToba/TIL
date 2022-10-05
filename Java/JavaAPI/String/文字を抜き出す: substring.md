## substring

String.substringメソッドを用いることで、特定の文字を抽出することができる。

第一引数に開始点、第二引数に終了点を指定する。第二引数を指定しなかった場合は、第一引数から後ろすべてが抽出の対象となる。

(n, m) であれば、n + 1文字目からm文字目までを抽出することになる

```Java
class Test{

public static void main(String[] args){

	String text = "Hello World"; //　最初の文字は0番目扱い
	String target1 = text.substring(0,5); // Hello
	String target2 = text.substring(6); // World
	String target3 = text.subString(0,text.indexOf(" ")); //Hello
	
	}
}
```
