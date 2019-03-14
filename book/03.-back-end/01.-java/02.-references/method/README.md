# Method

## instanceof

참조변수가 참조하는 인스턴스의 실제 타입을 알아보기 위해 사용

```java
class Car {
  String color;
  int door;
}

class Sedan extends Car {
  void driveSedan() {
    System.out.println("Start Sedan");
  }
}
class SportsCar extends Car {
  void driveSportCar() {
    System.out.println("Start Sports Car");
  }
}
```

```java
Sedan sedan = new Sedan();
SportsCar sportsCar = new SportsCar();

isCar(sedan);
isCar(sportsCar);
```

```java
void isCar(Car car) {
  if (car instanceof Sedan) {
    Sedan s = (Sedan) car;
    s.driveSedan();
  } else if (car instanceof SportsCar) {
    SportsCar p = (SportsCar) car;
    p.driveSportCar();
  }
}
```

결과

```java
// Start Sedan
// Start Sports Car
```

> ### 참고자료
> <https://arabiannight.tistory.com/entry/301>