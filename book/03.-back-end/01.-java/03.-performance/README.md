# Performance

## String / StringBuffer / StringBuilder 의 사용

문자열을 더하는 식에는 `string` 보다는 `stringBuffer` 나 `stringBuilder` 을 사용해야 한다.

`string` 은 새로운 값을 할당할 때마다 새로 생성되기 때문 \(클래스의 메모리 참조 주소가 바뀜\)

`stringBuffer` 나 `stringBuilder` 는 값을 메모리에 append 하는 방식으로 [클래스를 별도로 생성하지 않는다.](/book/03.-back-end/01.-java/02.-references/immutable.html)

`stringBuilder` 는 변경 가능한 문자열로 synchronization 이 적용되지 않는다.

`stringBuffer` 는 _**멀티쓰레드 환경에서 안정적**_ 이다.

## try-finally 보다는 try-with-resources 를 사용 (Java 7)

향샹된 예외처리문으로 입출력 처리시 예외가 발생하면 JVM 이 자동으로 `close` 메소드를 호출하여 자원을 반납시켜 줍니다.

이때 `try()` 구문안에는 `AutoCloseable` 인터페이스를 구현한 객체여야 한다.

```java
public class MyResource implements AutoCloseable {
  public void close() throws Exception {
    System.out.println("Closeing!");
  }
}
```

```java
try (MyResource res = new MyResource()){
  // use the code
}
```

> `AutoCloseable` Class 는 별도의 문서를 참고하도록 한다.