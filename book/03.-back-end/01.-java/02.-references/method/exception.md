# Exception

Java 에서는 기본적으로 2가지의 에러 유형이 있다.

## Checked Exception

`Checked Exception` 는 외부 환경에 의해 미리 예상 되는 오류이다.

예를 들면 `IOException` `ClassNotFoundException` 등과 같이 _**반드시 예외처리가 필요하다.**_

* IOException
* SQLException

## Unchecked Exception (Runtime Exception)

`Unchecked Exception` 는 프로그램 로직상의 문제로 일어나는 로직상의 오류로써 미리 예상할 수 없다.

대표적으로 `RuntimeException` 과 같이 프로그램 실행중에 일어나며 _**반드시 예외처리를 필요로 하지 않는다.**_

* NullPointerException
* IllegalArgumentException
* IndexOutOfBoundException
* SystemException

> 예외처리한 객체는 작업이 끝난후 모드 GC 의 대상이 된다.

||Checked Exception|Unchecked Exception|
|--|--|--|
|처리여부|반드시 예외처리가 필요|명시적인 처리를 강제하지 않음|
|확인시점|컴파일 단계|실행단계|
|예외 발생 시<br>트랜잭션 여부|roll-back 하지 않음|roll-back 처리|
|대표적인 예외|`Exception` 의 상속을 받는 하위 클래스 중<br>`Runtime Exception`을 제외한 모든 예외|`Runtime Exception` 의 하위 예외 클래스|

> ### 참고자료
> <http://www.nextree.co.kr/p3239/>