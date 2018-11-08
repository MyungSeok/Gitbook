# 01. General

## 문 과 식 의 차이

* 문
  * 코드 엔진에서 해석하고 버리는 힌트 같은 것 (Java, Javascript, C, ... )
* 식
  * 변수에 할당되어 저장 된다 (Ruby, Kotlin, ... )

### Stack 과 Heap 의 비교

||Stack|Heap|
|--|--|--|
|접근 속도|빠른 접근|느린 접근|
|메모리 제한|제한적|제한 없음|
|Resize 가능|불가|가능 (파편화 가능성)|
|특징|지역변수에만 할당|전역적 접근|

### List 와 Map 의 비교

#### List

* 순차적으로 데이터를 저장한다.
* 값의 중복이 허용된다.
* 순차적인 접근이 필요할 경우 사용

#### Map

* 키를 중복으로 저장불가 하다. (값은 가능)
* 빈 공간을 찾아서 저장하기 때문에 List 보다는 데이터 저장속도가 느릴수 있다.
* 키값을 통해서 빠르게 데이터 검색 가능

## RBAC (Role Based Access Control : 역활기반 접근 통제)

접근하려는 사용자와 자원이 어떻게 상호작용하는지 결정하여 중앙에서 집중적으로 작용한다.

* 역할 할당 (Role Assignment)
* 역할 권한 부여 (Role Authorization)
* 권한 부여 (Permission Authorization)

## MAC (Mandatory Access Control : 강제적 접근 통제)

## DAC (Discretionary Access Control : 임의적 접근 통제)

## Separation Of Concern (관심의 분리)

SOA (Service-Oriented Architecture : 서비스 지향 아키텍처) 의 핵심 원칙중의 하나로 _**관심이 다른것은 가능한 분리하여 서로 영향을 주지 않도록 하며, 관심이 같은 것은 하나의 관련 객체로 모이도록 설계나 구현**_ 을 하는 것

## TDD / BDD / DDD

테스트 주도 개발 방법론들이다.

### TDD (Test Driven Development)

* 테스트 주도 개발 방법론
* 테스트 코드를 먼저 작성하고 해당 테스트 코드에 맞게 개발을 진행한다.

## BDD (Behavior Driven Development)

* 동작 지향 개발 방법론
* 소프트웨어의 품질을 향상 시키기 위해 개발자간의 협력 가능한 Agile Software Development 기법이다.
* BDD 의 목표는 TDD 를 수행하기 위한 것으로, TDD 를 수행하기 위해 BDD 를 통한 행위 자체를 변경 가능하다.

## Unsinged Int

부호가 없는 정수형의 값만 가진다.