# Reflection

리플렉션이란 객체의 클래서 정보를 분석해 내는 프로그램 기법을 말한다.

> _**reflection**_ 의 사전적인 의미투영 및 반사입니다.

이는 실행중인 자바 프로그램의 내부를 검사하고 그 속성을 수정할 수 있도록 한다.

쉽게 말해 _**객체를 통하여 클래스의 정보를 역으로 분석해내는 프로그래밍 기법**_ 을 말한다.

```java
Class aClass = Test.class;

Class myObjClass = Class.forName(className);
Package pkgOfAClass = aClass.getPackage();
```

## 사용

동적으로 로딩하고 동적으로 실행하고 싶을때 주로 사용된다.

재사용성, 확장성, 생산성, 유연성 등이 극대화될 수 있는 곳이여야 효과적이다.

## 이슈

Runtime 시에 동적으로 원하는 라이브러리를 로딩할 수 잇는 장점이 있지만  
컴파일시에 탐색 (Detection) 이 안되어 Runtime Exception 이 생길수 있는 단점이 존재 한다.

보통은 동적로딩이 느리다고 전해진다 (확인불가)

> ### 참고자료
> <https://gyrfalcon.tistory.com/entry/Java-Reflection>  
> <https://asfirstalways.tistory.com/221>