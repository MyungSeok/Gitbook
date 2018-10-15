# JVM (Java Vertual Machine)

프로그램을 실행하기 위해 물리적 머신 (컴퓨터) 과 유사하게 만든 머신을 소프트웨어로 구현한 것

## 특징

* 자바의 가상머신으로 OS 에 종속적이지 않아 독립적으로 운영된다.
* GC (Garbage Collection) 은 사용자에 의해 명시되지 않으며 자동으로 메모리 관리가 된다.

## JVM 구조

프로그램이 실행되면 JVM 은 _**OS 로부터 프로그램이 필요로하는 메모리를 할당**_ 받고, JVM 은 이 메모리를 _**용도에 따라 여러 영역으로 나누어 관리**_ 한다.

!["JVM 구조"](../../../.gitbook/assets/jvm.png)

Java 로 작성한 코드는 _**Class Loader 가 컴파일된 Java Byte Code 를 Runtime Data Areas 에 로드하고 Excution Engine 이 Java Byte Code 를 실행**_

### Class Loader (클래스 로더)

자바는 Runtime 시에 해당 Class 를 로드하고 링크하는 Dynamic Loading 특징이 있다.  
이 Dynamic Loading 특징을 담당하는 부분이 Class Loader 이다.  
Class Loader 는 로드된 클래스를 보관하는 Namespace 를 갖는데, 이미 로드된 클래스 인지 확인하기 위하여 Namespace 에 보관된 `FQCN` 을 기준으로 클래스를 찾는다.

> FQCN (Fully Qualified Class Name) ?
>  
> 클래스가 속한 패키지명을 모두 포함한 이름을 말한다.  
> 보통 `java.lang.String s = new java.lang.String();` 과 같이 Alias Name (축약) 형이 아닌 패키지를 모두 포함한 경로  
> Class Loader 에서는 비록 FQCN 이 같더라도 Namespace 가 다르면 다른 클래스로 간주

Class Loader 는 작성한 Java Byte Code 를 JVM 메모리상에 올려주는 역활을 한다.

Class Loader 가 Class Load 를 요청 받으면, 아래 순서대로 검색을 한다.

```mermaid
  graph LR;
    A["Class Loader Cache"]-->B["Parent Class Loader"];
    B-->C["Self"];
```

부트스트랩 클래스 로더까지 확인해도 없으면 요청 받은 클래스 로더가 파일 시스템에서 해당 클래스를 찾음

> Class Loader 는 Unload 기능을 하지 않는다. (Unload 는 GC 자동으로 함)

## Runtime Data Areas

* Class
* Stack
* Heap
* Native Method
* PC Register

> Reference
>
> http://limkydev.tistory.com/51

## GC (Garbage Collector)

`stop-the-world` 을 실행하면 GC 를 실행하는 `thread` 를 제외한 나머지 `thread` 는 모두 작업을 멈춘다.

GC 작업을 완료한 이후에는 중단됬던 작업을 다시 시작한다.

JAVA 프로그램 코드에서는 메모리를 명시적으로 지정하여 해제하지 않는다.  
이는 GC 내부인 기준에 의해서만 메모리를 해제하는 작업을 하는데 기준은 다음과 같다.


> `stop-the-world` 란?  
> GC 를 실행하기 위해 JVM 이 애플리케이션 실행을 멈추는 것이다.

> Reference
>
> https://d2.naver.com/helloworld/1329