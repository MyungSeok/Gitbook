# Multi Thread

Java 에서는 Multi Thread 환경을 만들어 사용하는 방법은 대표적으로 2가지 방법을 많이 사용한다.

## Thread Class 를 상속받아 사용

### 구현 순서

1. Thread Class 를 상속 받아 내가 시킬 일을 해줄 Class 를 하나 만든다.
2. 위에서 만든 Class 에 `run` Method 안에 시킬 일을 정의해 준다.
3. 메인 Thread 에서 위에서 만는 Class 의 `start` Method 를 호출한다.

> 반드시 `start` 메소드로 실행을 해야 한다.  
> `run` 메소드를 실행하면 메인 Thread 에서 돌아가므로 의미가 없다.

```java
static class AddThread extends Thread {
  @Override
  public void run() {
    int sum = 0;

    for (int i = 1; i < 11; ++i) {
      sum += i;

      System.out.printf("Add Sum is %d\r\n", sum);
    }
  }
}
```

```java
AddThread at = new AddThread();
at.start();
```

## Runnable 인터페이스를 구현하여 사용

### 구현순서

1. 우선 `Runnable` Interface 를 구현할 Class 를 하나 생성한다.
2. 위에서 만든 Class 의 `run` Method 에 시킬 일을 정의한다.
3. 해당 Class 를 생성하고 Thread 를 생성할 때 인자로 넣어서 생성한다.
4. 메인 Thread에서 위에서 만든 Class 의 `start` Method 를 호출한다.

```java
static class AddThreadRunnable implements Runnable {
  @Override
  public void run() {
    int sum = 0;

    for (int i = 1; i < 11; ++i) {
      sum += i;

      System.out.printf("Add Sum is Runnable %d\r\n", sum);
    }
  }
}
```

```java
Runnable ar = new AddThreadRunnable();
Thread atr = new Thread(ar);

atr.start();
```

> Reference
> https://post.naver.com/viewer/postView.nhn?volumeNo=7852076&memberNo=30800755