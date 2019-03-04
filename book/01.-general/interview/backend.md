# BE 면접 질문

## Integer 의 바이트는 ?

* 4Byte

## short integer 의 최하 / 최상 값은 ?

* -32,768 ~ 32,767

## unsigned Integer 는 ?

* 일반적으로 unsigned int 는 부호비트를 값 비트로 쓸수 있어서 _**2^32 -1**_ (4294967295) 값을 가진다.
* Java 에서는 unsigned int 값이 없으며 long 으로 대체하여 사용한다.

## Compiler 와 Interpreter 의 차이점

* Compiler 는 문서 전체를 다 읽어 기계어로 번역한다. (구문 -> 목적 프로그램)
* Interpreter 는 한줄한줄 행 단위로 읽어서 처리한다. (구문 -> 명령문)

## Java 에서 instanceof 연산자란 ?

* 참조 변수가 실제로 참조하고 있는 인스턴스의 실제 타입을 알아보기 위해 instanceof 연산자를 사용

## Stack 과 Heap Memory 장단점과 해제 방법을 설명

* Stack
  * 빠른접근, cpu 에 의해 관리, 지정된 크기, resize 불가
  * 해제 : 자동
* Heap
  * 전역적으로 접근 가능, 메모리 크기 제한 없음, resize 가능하나 파편화가 가능
  * 해제 : 수동

## Quick Sort 란 무엇이고 시간복잡도는 어떻게 되는지 설명

* 일반적으로 정렬 알고리즘중에서 빠르다고 알려진 알고리즘
* 시간 복잡도
  * Best : n log n
  * Worst : n^2
  * Average : n log n
* Pivot 선택노드가 속도에 영향을 줄 수 있음

## Java 에서 `public static void main( ... )` 으로 시작할 때 `public` 과 `static` 을 붙이는 이유는 ?

* 메인 메서드는 진입점 (Entry Point) 를 뜻하며 접근제어자가 `public` 이 되어야 함
* 함수에 static 을 붙이게 되면 instance 화 되기 전에 호출 가능하다.
* 클래스 멤버는 메모리에 로딩된 다음에 사용이 가능하다
* main 함수는 프로그램 최초에 호출되는 함수이기 때문에 객체 생성 이전에 호출할 수 있어야 한다.
* static 이 붙은 클래스나 메서드, 변수는 컴파일시 자동으로 로딩

## 관심의 분리 (Separation Of Concern) 에 대해 설명하고 예를 들어 설명

* 서비스 지향 아키텍쳐 (SOA : Service-Oriented Architecture) 의 핵심 원칙
* 관심이 같은것은 뭉치고 관심사가 다른것은 서로 떨어져 영향을 주지 않도록 설계 및 구현을 하는것

## AOP 이란 ?

* 비지니스 로직과 공통모듈을 분리하여 핵심로직에 영향을 미치지 않고 사이사이에 공통모듈을 효과적으로 잘 끼워넣는 개발방법
* 공통모듈은 보안, 인증, 로깅 같은 것을 만든 후에 코드 밖에서 이 모듈을 비지니스 로직에 삽입하는것이 AOP 개발 방법이다.
* 코드 밖에서 설정된다는것이 핵심이며 프로그램 흐름을 파악하기 힘들기 때문에 AOP 사용이 많아질경우 유지보수가 어렵다.

## BDD 란 무엇이고 TDD 와 어떤 연관이 있나 ?

* Behavior Driven Development (행위 주도 개발) 의 약자이다.
* BDD 는 소프트웨어의 수행을 위한 것으로 TDD 접근법을 전환한것이다.

## `String` vs `StringBuffer` 차이점은 ?

* String Class 인 경우 Character 조작을 위한 것이며 단순한 상태값을 가지고 있는 불변 속성이다.
* StringBuffer Class 인 경우 문자열을 재구성하기 위한 것이며 수정이 가능하다.

## `CheckedException` 과 `UncheckedException` 의 차이와 용도를 설명

* Checked Exception
  * 외부상황에 의해 미리 예상 가능한 오류이다
  * 예) 디스크 오류, 네트워크 오류등 로직 상의 오류와는 무관하게 발생하는 에러.
  * IOException, ClassNotFoundException, CloneNotSupportedException등등
  * RuntimeException을 제외한 Exception을 직접 상속한 모든 예외 클래스는 Checked Exception.
* Unchecked Exception
  * 프로그램 로직 상에 문제로 인해 생기는 오류이다.
  * RuntimeException 이하 모든 하위클래스는 Unchecked exception이다.
  * 발생한 예외에 대하여 반드시 코드상에서 예외 처리를 하도록 요구하지 않는다.
  * NullPointerException의 경우 null을 참조하려는 시도는 프로그램 코드 자체가 잘못된 것.
  * 이런 예방 할 수 없는 오류 조건들은 로직 상에서 처리를 요구

## 객체 재사용이란 무엇인가 ?

* Singleton Instance 와 같이 최초에 한번 생성한 후 재사용하는 것
* ThreadPool, ConnectionPool 등 이외에도 코드내에서 객체를 재사용하는 방법이 있다.

```java
StringBuffer sb = new StringBuffer();
sb.append(“data1”);
System.out.println(sb);
sb.setLength(0);
```