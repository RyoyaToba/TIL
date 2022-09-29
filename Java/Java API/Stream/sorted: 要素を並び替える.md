## sorted

Collection要素の並び変えに用いる。Collectionsのsortメソッドでも同様の実装が可能であるが、
今回のようにStreamAPIを用いた実装の方が、簡潔に記述することができる。


**昇順に並び替える場合**

```Java
public class sample{

  public static void main (String args[]){
      List<int> numberList = List.of(20, 40, 30, 10, 50);
      
      numberList.Stream()
                .sorted()　// defaultで昇順になる (もしくはComparator.naturalOrder())
                .forEach(System.out::println) // (10, 20, 30, 40, 50)
  }
}
```

**降順に並び替える場合**

```Java
public class sample{

  public static void main (String args[]){
      List<int> numberList = List.of(20, 40, 30, 10, 50);
      
      numberList.Stream()
                .sorted(Comparator.reverseOrder())　// defaultで昇順になる
                .forEach(System.out::println) // (50, 40, 30, 20, 10)
  }
}
```

**複数条件によるソート**

Stdentクラスの作成

```Java
public class Student {

    private int age;        //年齢
    private int birthDay;   //誕生日
    private String name;    //名前

    //コンストラクタ
    public Student(int age, int birthDay, String name) {
        this.age = age;
        this.birthDay = birthDay;
        this.name = name;
    }

    //ゲッター・セッター
    public int getAge() { return age;}
    public void setAge(int age) { this.age = age;}
    public int getBirthDay() { return birthDay;}
    public void setBirthDay(int birthDay) {this.birthDay = birthDay;}
    public String getName() {return name;}
    public void setName(String name) {this.name = name;}

    @Override
    public String toString(){
        return this.age + ":" + this.birthDay + ":" + this.name;
    }
}
```

並び替える

```Java
List<Student> StudentList = new ArrayList<>();

//Studentリストにデータを詰める。
StudentList.add(new Student(17, 20051029, "Yamada"));
StudentList.add(new Student(19, 20031101, "Sato"));
StudentList.add(new Student(17, 20050326, "Ito"));
StudentList.add(new Student(18, 20040610, "Kato"));
StudentList.add(new Student(16, 20060514, "Goto"));
StudentList.add(new Studnet(19, 20030628, "Saito"));
StudentList.add(new Student(16, 20060112, "Sasaki"));

StudentList.stream()
    //年齢の降順かつ、誕生日の降順に並び替える。
    .sorted(Comparator.comparing(Student::getAge).reversed()
    .thenComparing(Comparator.comparing(Student::getBirthDay).reversed()))
    .collect(Collectors.toList())
    .forEach(System.out::println);
```

実行結果

```
19:20031101:Sato
19:20030628:Saito
18:20040610:Kato
17:20051029:Yamada
17:20050326:Ito
16:20060514:Goto
16:20060112:Sasaki
```

## 参考

https://nompor.com/2022/05/29/post-7191/

https://www.zunouissiki.com/how-to-use-sorted-of-streamapi/
