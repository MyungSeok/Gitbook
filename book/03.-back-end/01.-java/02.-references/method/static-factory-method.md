# 정적 팩토리 메소드 (Static Factory Method)

기본적으로 Class 의 Instance 를 얻는 전통적인 수단은 public 생성자이다.

클래스는 생성자와 별도로 정적 팩토리 메서드 (static factory method) 를 생성할 수 있다.

## 사용

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
`immutable` 객체를 캐시해서 쓰고 있거나 혹은 아래와 같이 _**singleton design pattern**_ 을 이용하여 사용도 가능하다.

```java
class Person {
  private final Person p = new Person();

  public static Person getInstance() {
    return this.p;
  }
}
```

아래와 같이 리턴하는 클래스의 타입을 유연하게 지정가능하다.

```java
class OrderUtil {
  public static Discount createDiscountItem(String code) throws Exception {
    if (!isValidCode(code)) {
      throw new Exception("Wrong discount code !!");
    }

    if (isCoupon(code)) {
      return new Coupon(1000);
      return new Point(500);
    }
  }
}

class Coupon extends Discount { ... }
class Point extends Discount { ... }
```

## 단점

* 상속을 하려면 `public` 이나 `protected` 생성자각 필요하니 정적 팩토리 메서드만 지원하면 하위 클래스를 만들수 없다.
* 정적 팩토리 메서드는 프로그래머가 찾기 어렵다.
  * 암묵적으로 대표적인 명명 규칙들에 의해 메서드 네이밍을 하는것이 일반적이다.
  * `from`, `of`, `valueOf`, `instance`, `getInstance`, `create`, `getType` ...

> ### 관련출처
> Effective Java 3rd  
> <https://johngrib.github.io/wiki/static-factory-method-pattern/>  
> <https://mommoo.tistory.com/53>