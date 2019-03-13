# AutoCloseable

파일 또는 소켓 핸들 등의 자원들을 종료할 때까지 보관하는 객체이다.  
AutoCloseable 객체의 `close` 메소드는 `try-with-resources` 블럭을 종료할 때 자동으로 호출 된다.

이 구조는 리소스의 고갈 및 다른 예외들까지 발생할 수 있는 에러들의 해소를 즉각적으로 보장한다.

`try-with-resource` 구문과 같이 사용한다.

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

> ### 참고자료
> <https://hyoj.github.io/blog/java/basic/java7-autocloseable.html#method-summary>