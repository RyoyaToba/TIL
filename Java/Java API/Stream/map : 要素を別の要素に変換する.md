## map

mapメソッドを使用すると要素の変換を実行できる。

### 前提　RaceInfoクラスの定義

```Java
public class RaceInfo {
    
    //フィールド変数
    public String raceId;
    public String raceDay;
    public String raceNumber;
    public String raceName;
    public String raceDetail;
    public String field;
    
    // コンストラクタ
    public RaceInfo(String raceId, String raceDay, String raceNumber, String raceName, String raceDetail, String field){
        this.raceId = raceId;
        this.raceDay = raceDay;
        this.raceNumber = raceNumber;
        this.raceName = raceName;
        this.raceDetail = raceDetail;
        this.field = field;
    }
    
    // 結果の表示用toString
    public String toString(){
        return "raceId = " + raceId + " " + "raceDay = " + raceDay + " " + "raceNumber = " + raceNumber + " "  + "raceName = " + raceName + " " + "raceDetail = " + raceDetail + " " + "field = " + field;
    }

    // raceInfoListの作成をstaticメソッドで定義
    public static List<RaceInfo> raceInfoList(){
        return List.of(
            new RaceInfo("202101010101","6月12日(土)","札幌01R","3歳未勝利","芝1200m","馬場:良")
            ,new RaceInfo("202101010102","6月12日(土)","札幌02R","3歳未勝利","ダ1700m","馬場:良")
            ,new RaceInfo("202101010103","6月12日(土)","札幌03R","3歳未勝利","ダ1000m","馬場:良")
            ,new RaceInfo("202101010104","6月12日(土)","札幌04R","3歳未勝利","芝2000m","馬場:良")
        );
    }
}
```

mapメソッドを使って出力内容を編集する。今回はraceNumberを全件出力する。

```Java
public static void mapSample(){
    List<RaceInfo> raceInfo = RaceInfo.raceInfoList();
    raceInfo.stream()
       .map(e -> e.raceNumber)
       .forEach(System.out::println);
}
```

```console
札幌01R
札幌02R
札幌03R
札幌04R
```

