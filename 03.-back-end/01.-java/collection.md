# Collection

`Collection` 인터페이스를 상속 받은 구현체 `List` 와 `Set` 을 기준으로 나뉜다.

```mermaid
  graph LR
  A["Collection"] --> B["List"]
  B --> D["Linked List"]
  B --> E["Stack"]
  B --> F["Array List"]
  B --> G["Vector"]
  A --> C["SET"]
  C --> H["Hash Set"]
  C --> I["Sorted Set"]
  I --> J["Tree Set"]
```

## List

순서가 있는 `Collectaion` (삽입된 순서)  
Data 를 중복해서 포함할 수 있다.

* Linked List
* Stack
  * 후입선출 (LIFO : Last-In First-Out) 구조로 되어 있다.
* ArrayList
  * 동기화를 보장하지 않는다.
  * 배열의 동적 메모리 증가 기능을 구현한 클래스
* Vector  
  * 자동으로 동기화를 보장해 준다.
  * ArrayList 의 동기화가 보장되도록 최적화한 클래스
  * JDK 5.0 이후부터 Auto Boxing / UnBoxing 기능을 지원
* Tree Set
  * 정렬 기능을 지원 (데이터들이 자동으로 오름차순으로 정렬)

> AutoBoxing
> 기본 데이터 타입을 Wrapper 클래스형의 객체로 자동 변환해주는 기능

## Set

집합적인 개념의 Collection  
순서의 의미가 없다.  
Data 를 중복해서 포함할 수 없다.

* Hash Set
  * Hash 기법을 사용하지만 Set 인터페이스를 구현하고 있다.
* Sorted Set
  * 정렬 기능을 지원함

## Map

`Key` 와 `Value` 의 형태로 데이터를 관리한다.

* HashMap
  * 동기화 보장이 안된다.
* Hashtable
  * 동기화 보장이 된다. (멀티스레드 환경에서 안정적)
* TreeMap
  * 정렬 기능을 지원함

```mermaid
  graph LR
  A["Map"] --> B["HashMap"]
  A --> C["Hashtable"]
  A --> D["Sorted Map"]
  D --> E["Tree Map"]
```

> Reference  
> http://withwani.tistory.com/150