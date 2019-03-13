# Immutable Class (불변 객체)

생성후 변경 불가능한 객체로서 대표적으로 _`String`_, _`Boolean`_, _`Integer`_, _`Float`_, _`Long`_ 등등이 있다.

> HEAP 영역에서의 값이 바뀌는건 아니다.

## String vs StringBuffer

String 은 Immutable 이고 StringBuffer 는 아니다.
이는 객체를 새로 생성할 필요가 없는 StringBuffer 가 더 빠르다는 이야기이다.

```java
StringBuffer b = new StringBuffer();
StringBuffer a = b.append("test");

System.out.println(a == b);     // true
```

> ### 참고자료
> <https://hashcode.co.kr/questions/727/자바에서-immutable이-뭔가요>