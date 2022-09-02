　## forEach

forEachメソッドによってリスト内の要素を全件表示することができる。

### 前提 RaceInfoクラスの定義

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
### forEach使用時

```Java
public class Stream{
   public static void forEachSample(){
       List<RaceInfo> raceInfoList = RaceInfo.raceInfoList();
       raceInfoList.stream().forEach(System.out::println);
   }
}
``` 
### 出力結果

```console
raceId = 202101010101 raceDay = 6月12日(土) raceNumber = 札幌01R raceName = 3歳未勝利 raceDetail = 芝1200m field = 馬場:良
raceId = 202101010102 raceDay = 6月12日(土) raceNumber = 札幌02R raceName = 3歳未勝利 raceDetail = ダ1700m field = 馬場:良
raceId = 202101010103 raceDay = 6月12日(土) raceNumber = 札幌03R raceName = 3歳未勝利 raceDetail = ダ1000m field = 馬場:良
raceId = 202101010104 raceDay = 6月12日(土) raceNumber = 札幌04R raceName = 3歳未勝利 raceDetail = 芝2000m field = 馬場:良
```
