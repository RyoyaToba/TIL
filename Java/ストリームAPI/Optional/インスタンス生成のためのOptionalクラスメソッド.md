## インスタンス生成のためのOptionalクラスメソッド


メソッド|説明
--|--
static <T> Optional <T> empty()|空のOptionalのインスタンスを生成し、参照を戻す
static <T> Optional <T> of(T value)|null以外の値を持ったOptionalのインスタンスを生成し、参照を戻す
static <T> Optional <T> ofNullable(T value)|値を持っているか、値がnullの場合は、空のOptionalのインスタンスを生成し、参照を戻す
  

