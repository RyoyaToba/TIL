## groupingBy

ストリームの要素を指定した要素によってグルーピングする機能。

Departmentクラスの作成

```Java
public class Department {
  private String name;
  public Department(String name){
    this.name = name;
  }
  public String getName(){
    return name;
  }
  @Override
  public int hashCode(){
    return name.hashCode();
  }
  @Override
  public boolean equals(Object obj){
    if (obj instanceof Department) {
      Department other = (Department) obj;
      return this.name.equals(other.name);
    }
    return false;
  }
}
```

実行クラス（import省略）

```Java
public class Sample{
  public static void main(String[] args){
    Department tokyo = new Department("Tokyo");
    Department osaka = new Department("Osaka");
    List<Employee> list = List.of(
      new Employee("Johnny", tokyo),
      new Employee("Bond", osaka),
      new Employee("Mickey", tokyo),
      new Employee("Sara", osaka)
    );
    Map<Depertment, List<Employee>> result =
      list.stream().collect(
        Collectors.groupingBy(Employee::getDept)
      );
  }
}
```

以上のコードにより、Department名によってグルーピングされ、keyをDepartment名、valueをListとしたMapを作成する。

実行結果

```console
Department@4d3cc46=[Employee{name='Johnny', dept=Department@4d3cc46}, Employee{name='Mickey', dept=Department@4d3cc46}], 

Department@48f00f3=[Employee{name='Bond', dept=Department@48f00f3}, Employee{name='Sara', dept=Department@48f00f3}]}

```
