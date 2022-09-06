## filter

filterメソッドを利用することで、要素に対して絞り込みを行うことができる。

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

filterメソッドを使い、芝レースのみを出力する

```Java
public<RaceInfo> filterSample(){

  List<RaceInfo> raceInfoList = RaceInfo.raceInfoList();
  raceInfo.stream()　// streamの生成
    .filter(e -> e.raceDetail.contains("芝")) // filterによる絞り込み
    .forEach(System.out::println); // 全件出力
}
```

```コンソール
raceId = 202101010101 raceDay = 6月12日(土) raceNumber = 札幌01R raceName = 3歳未勝利 raceDetail = 芝1200m field = 馬場:良
raceId = 202101010104 raceDay = 6月12日(土) raceNumber = 札幌04R raceName = 3歳未勝利 raceDetail = 芝2000m field = 馬場:良
```
