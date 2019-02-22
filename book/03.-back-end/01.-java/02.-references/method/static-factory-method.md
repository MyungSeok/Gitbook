# 정적 팩토리 메소드 (Static Factory Method)

기본적으로 Class 의 Instance 를 얻는 전통적인 수단은 public 생성자이다.

클래스는 생성자와 별도로 정적 팩토리 메서드 (static factory method) 를 생성할 수 있다.

```java
class Character() {
  int strength, dexterity, consitution, intelligence;

  public Character(int strength, int dexterity, int consitution, int intelligence) {
    this.strength = strength;
    this.dexterity = dexterity;
    this.consitution = consitution;
    this.intelligence = intelligence;
  }

  public static Character newWarrior() {
    return new Character(15, 5, 10, 3);
  }

  public static Character newMage() {
    return new Character(3, 10, 5, 15);
  }
}
```

```java
Character warrior = Character.newWarrior();
Character mage = Character.newMage();
```

위 코드는 정적 팩토리 메서드를 호출할 때 마다 `new` 연산을 하게 되는데  
`immutable` 객체를 캐시해서 쓰고 있거나 _**singleton design pattern**_ 을 이용하여 사용도 가능하다.

```java
class Person {
  private final Person p = new Person();

  public static Person getInstance() {
    return this.p;
  }
}
```

> ### 관련출처
> Effective Java 3rd  
> <https://johngrib.github.io/wiki/static-factory-method-pattern/>
> <https://mommoo.tistory.com/53>