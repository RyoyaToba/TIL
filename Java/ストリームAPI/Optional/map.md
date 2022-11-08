## map

mapメソッドは、Function型の引数を受け取り、処理結果を持った新しいOptionalのインスタンスを生成し、その参照を戻す。

```Java
public class MapTest{
  public static void main(String[] args){
    Optional<String> sample = Optional.of("test");
    Optional<String> result = sample.map(
                      str -> str.toUpperCase());
    System.out.println(sample.get());
    System.out.println(result.get());
  }
}
```

## 使用例

非常に納得してOptional.mapを使えた場面。

findByEmailメソッドはDBからメールアドレスを引数にしてAdministratorEntityを戻す。

このメソッド内ではEntityからDTOへの変換処理をConvertFromEntityToDtoUtility.returnAdministratorDtoメソッドにより実行するが、もしEmailでデータが該当しない場合はnullが戻されるので
ConvertFromEntityToDtoUtility.returnAdministratorDtoメソッドでNullPointerExceptionが発生し、例外をスローする。

そこで、Optionalでラッピングし、mapメソッドを使用してconsumer型ラムダ式で変換処理を行い、orElseメソッドを使用してDTOを新たにインスタンス化する。

```Java
public AdministratorDto findByEmail(String email) {
		// 入力値が間違いだった場合、nullが帰ってくるので、Optionalを使用
		Optional<AdministratorEntity> entity = Optional.ofNullable(adminMapper.findByEmail(email));
		// nullの状態でConvertFromEntityToDtoUtilityのメソッドを呼ぶとエラーになるので、orElseで処理
		return entity.map(x -> ConvertFromEntityToDtoUtility.returnAdministratorDto(x)).orElse(new AdministratorDto());
	}
```

