## insert

➀　StringをStringBuilderに変換

➁　StringBuilderのinsertメソッドを使う

insertメソッドは第一引数に挿入したい部分の番号、第二引数に挿入したい文字を入れる


 使用用途
 
 スクレイピングによって自動取得したデータが存在し、SQLを作成する際に、「'」が含まれている名前をエスケープしたい時

```Java
class Test{
	public static void main(String[] args){
		if (horseName.contains("'")) { //含まれているか判定
			int dotNumber = horseName.indexOf("'"); //何文字目か
			StringBuilder sb = new StringBuilder(horseName); //StringBuilderに変換
			sb.insert(dotNumber, "'");  //特定の番号のところにインサート
			horseName = sb.toString();  //StringBuilderをStringに変換
		}
	}
}
```
