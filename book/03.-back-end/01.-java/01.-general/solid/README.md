# Solid

객체지향 4대 특성인 캡슐화, 상속, 추상화, 다형성 등을 이용하여 객체지향 프로그래밍 셜계를 도와주는 원칙들이 있다.  
이를 SOLID 원칙들이라 하며 자기 자신의 클래스의 응집도를 높이고, 타 클래스의 결합도를 낮추는 _**High-Cohesion - Loose Coupling**_ 원칙을 객체 지향관점에서 도입한것이다.

SOLID 5대 원칙 (객체 지향 설계 5원칙)

* [SRP (Single Reponsibility Principle : 단일 책임의 원칙)]((/book/03.-back-end/01.-java/01.-general/solid/srp.html))
* [OCP (Open Closed Principle : 개방 폐쇄의 원칙)](/book/03.-back-end/01.-java/01.-general/solid/ocp.html)
* [LSP (Liskov Substitution Principle : 리스코프 치환의 원칙)](/book/03.-back-end/01.-java/01.-general/solid/lsp.html)
* [ISP (Interface Segregation Principle : 인터페이스 분리의 원칙)]((/book/03.-back-end/01.-java/01.-general/solid/isp.html))
* [DIP (Dependency Inversion Principle : 의존 역전의 원칙)]((/book/03.-back-end/01.-java/01.-general/solid/dip.html))

## SRP (Single Reponsibility Principle : 단일 책임의 원칙)

작성된 _**클래스는 하나의 기능만 가지며**_ 클래스가 제공하는 모든 서비스는 그 _**하나의 책임을 수행하는데 집중**_ 되어야 한다는것

> 리팩토링 (Refactoring) 을 통하여 해당 책임을 최상의 상태로 분배

## ISP (Interface Segregation Principle : 인터페이스 분리 원칙)

최소한의 의미에 맞는 인터페이스만 구현해야 한다.

> 클래스 인터페이스를 통한 분리  
> 객체 인터페이스를 통한 분리 

## DIP (Dependency Inversion Principle : 의존 역전 원칙)

하위 레벨모듈의 변경이 상위 레벨 모듈의 변경을 요구하는 역전현상

> Reference
> 
> http://www.nextree.co.kr/p6960/  
> http://limkydev.tistory.com/77  
> http://choipattern.blogspot.com/2013/08/solid.html