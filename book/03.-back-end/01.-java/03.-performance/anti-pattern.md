# 안티 패턴 (Anti-Pattern)

## 인스턴스 생성 사례

불변 (Immutable Class) 객체의 재사용을 한다.

생성후 변경 불가능한 객체로서 대표적으로 _`String`_, _`Boolean`_, _`Integer`_, _`Float`_, _`Long`_ 등등이 있다.

### 안티패턴

```java
String str = new String("bikini");
```

### 권장 패턴

```java
String str = "bikini";
```

> 최신 JVM 상에서는 고정 문자열일때 컴파일러가 처음부터 바이트 코드를 StringBuilder 로 변경되어 인스턴스가 생성되지 않는다.  
> 하지만 가급적 문자열 연산이 많다면 `StringBuilder` 를 권장

## 오토 박싱

박싱된 Warpper 형 보다는 원시 기본 타입을 사용한다.

```java
private static long sum() {
  Long sum = 0L;
  for (long i = 0; i <= Integer.MAX_VALUE; i++) {
    sum += i;
  }

  return sum;
}
```

### Stack Class 클래스의 메모리 누수

자기 메모리를 직접 관리하는 클래스라면 메모리 누수에 주의해야 한다.

* 캐시용도로 사용하는 객체는 `WeackHashMap` 을 사용
* 스택과 같은 객체는 사용후 `null` 로 참조해제를 시켜주도록 한다.

```java
public class Stack {
  private Object[] elements;
  ...
  public Object pop() {
    if (size == 0) {
      throw new EmptyStackException();
    }

    Object result = elements[--size];

    // 다 쓴 참조를 해제 해주도록 하자
    elements[--size] = null;

    return result;
  }
}
```

## Finalize Method

`finalize` 메소드에 의한 Collection 지연과 OOME (Out of Memory Exception) 발생 가능성 때문에 사용을 지양한다.

특정 Class 에서 finalize 메소드가 정의되어 있는 경우 해당 Class Type 의 Object 는 Gabege Collection 발생시 즉각적으로 Collction 되지 않는다.  
이는 Finalization Queue 에 들어간 후 Finalizer 에 의해 정리되는데 참조가 해제된 객체에 대해서도 _**`finalize` 메소드에 의해 GC 실행이 보장되지 않는다.**_

### 대안

`AutoCloseable` 을 구현해주고 클래스에서 인스턴스를 다 사용하면 `close` 메소드를 호출해준다.

> ### 참고자료
> <http://www.yunsobi.com/blog/entry/finalize-메소드의-오버라이딩을-자제해야하는-이유>