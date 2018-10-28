# 동기화 (Synchronized)

여러 Thread 가 한 개의 자원을 사용하고자 할 때 해당 Thread 만 제외하고 나머지 Thread 의 접근을 막는 방법이다.  
`synchronized` 키워드의 식별자를 사용해서 구현한다.

## Syntax

1. 함수에 사용하는 경우

```java
public synchronized void method() {
  /* statement */
}
```

2. 객체 변수에 사용하는 경우 

```java
private Object obj = new Object();

public void method() {
  synchronized (obj) {
    /* statement */
  }
}
```

## 장단점

### 장점

* `thread-safe` 하게 사용이 가능하여 사용자의 의도대로 프로그램의 흐름 제어가 가능하다.  

### 단점

* 프로그램의 성능저하를 일으킬 수 있다.
  * Java 내부적으로 메서드나 변수에 동기화를 하기 위해 block & unblock 처리를 하게되는데 이런 처리들을 통하여 소비되는 리소스가 프로그램 전반적인 성능에 영향을 준다.