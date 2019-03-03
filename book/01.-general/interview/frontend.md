# FE 면접 질문

## HTML Inline 요소와 Block 요소의 차이점 ?

* Inline 요소 : 브라우저에서 줄바꿈 없이 사용 가능한 엘리먼트 (`<td>`, `<b>`, `<a>` ...)
* Block 요소 : 브라우저에서 줄바끔 요소가 적용된 엘리먼트 (`<h>`, `<p>`, `<ul>`, `<li>` ...)

## 시맨틱 / 구조적 마크업

* 검색엔진을 통하여 검색이 문서검색 혹은 크롤링이 가능하게 접근성을 높인 마크업

## CSS Selector 에서 `body > div` 와 `body div` 의 차이점 ?

* body > div : 상위 노드가 body 태그를 가지는 div 태그
* body div : 상위 노드들 중에 body 태그를 가지는 div 태그

## CSS Position 중에 `static`, `relative`, `absolute`, `fixed` 의 차이점

* static : 포지션 설정을 하지 않았을 때 static
* relative : 상대적인 위치정보를 지정할때 사용
* absolute : 절대적인 위치정보를 지정할때 사용
* fixed : 고정된 위치정보를 지정할때 사용

## Reset CSS 란 ?

* 브라우저와 상관 없이 같은 모양을 나타내도록 CSS 를 초기화 하는것을 말함
* normalize css 라는 것과 유사하지만 강제로 초기화 시키는 reset css 와는 다르게 브라우저별 차이를 보이는 부분만 혹은 디자인적인 요소를 가미해서 reset 를 해준다는 차이점이 있다.

## CSS BOX MODEL 에 대해 설명

* Margin, Border, Padding, Width & Height 등을 그림을 그려서 설명

## IR 기법이란 ?

* 이미지를 대체할 엘리먼트를 배경 이미지로 설정하고 `<span>` 태그와 같은것으로 감싸면서 안보이게 처리

## 자바스크립트에서 null 과 undefined 차이점은 ?

* null 은 값이 `null` 이 할당된 것
* undefined 는 아무런 값이 할당되지 않는것
* `typeof` 로 확인해보면 `null` 은 `object` 로 확인되며 `undefined` 는 `undefined` 로 확인 가능

## `==` 와 `===` 의 차이점은 ?

* 값만 같다 혹은 타입까지 같다의 차이점이다.
* `==` 인 경우 자바스크립트에서는 타입이 같도록 형변환 과정을 거친후 값을 비교한다.
* 자바스크립트는 type safe 한 언어가 아니기 때문에 이러한 차이점이 있다. (java 는 type safe 한 언어임)

## Hoisting 이란 ?

* 함수의 선언과 변수의 선언이 해당 유효범위 상위로 옮겨지며 변수는 `undefined` 를 기본값으로 갖는 현상
* 함수의 표현식은 해당되지 않으며 같은 변수명과 함수명이 있을경우 변수명이 우선순위가 높아짐
* ES6 에서도 호이스팅이 지원안되는것이 정설이지만 TDZ 관점에서 없다고 봐도 무관하기 때문이다.

> **임의적 사각지대 \(TDZ : Temporal Dead Zone\)**
>
> 초기화 \(선언\) 가 되지 않는 객체들을 참조 할 수 없다.  
> \(호이스팅이 되지 않는것은 아님 - ES5 처럼 `undefined` 로 선 할당이 안됨\)

## DOM Event Model 에서 Bubbling 과 Capturing 의 차이점은 ?

* Bubbling : 자식노드 이벤트가 일어났을 경우 부모까지 이벤트가 전파되는 현상
* Capturing : 부모에서 자식으로 이벤트가 전달되는 현상
* DOM Delegation 으로 이어서 설명해야 함

## DOM Delegation 이란 ?

* Event Bubbling 이나 Capturing 이 일어날때 성능적인 이슈가 일어나거나 혹은 새로 추가되는 요쇼의 이벤트 바인딩이 주기적으로 필요할 경우 사용하는 이벤트 위임 방법이다.
* 이벤트 타겟의 부모에 이벤트를 걸어준 뒤 발생되는 이벤트 타입과 셀렉터를 체크하여 제어하는 식이다.

## 웹 성능 튜닝시 사용하는 도구는 ?

* 브라우저의 디버깅 도구, Google Pagespeed Insight, webpagetest.org dynatrace, showslow 등등을 활용

## Ajax 사용시 타겟의 URL 도메인이 다른 경우 해결 방법 ?

* JSONP, CORS 등을 이용하여 해결
* JSONP : DOM 트리에 추가되면 외부 스크립트를 로드할 수 있는것에서 착안하여 사용
  * 동일 출처 정책 (SOP : Same Origin Policy) 에 포함되지 않음

## 최근 FrontEnd 동향 / 라이브러리 / 프레임워크 / 스팩 / 기능 들의 관심있는 분야?

* vue > React > 템플릿 리터럴즈 (유인동) 이라고 보고 있다 (19/02)
* 바닐라 JS 를 좋아하기 때문에 ...

## 다음 상황을 구현하기 위한 방법을 서술하시요

```text
온라인 이메일 웹서비스를 구현한다고 가정하자. 이 페이지에는 리프레시 버튼이 하나 있는데, 이 버튼을 누르면 페이지를 다시 로딩하지 않고 새로 도착한 메일을 가져와 화면에 표시해주는 기능을 수행하여야 한다. 이를 어떻게 구현해야하는지 최대한 상세히 설명하시오. 서버측 구현은 이미 다 되어있다고 가정한다.
```

* DOM Event 처리 동작, DOM 조작, XHR 또는 JSONP / CORS 등등과 같은 내용들을 덧붙여 설명한다.

## 웹 접근성이란 ?

* 기본적인 웹 표준 준수 및 접근성에 대한 내용을 설명
* 시각 장애인들을 위한 TTS 나 약시, 색약, 지체 장애인들에 대한 대응
  * 바로가기링크
  * 명도대비 준수
  * 깜빡임 빈도
  * 클릭영역의 크기
* `alt` 대체 텍스트와 같은 기능적인 것들을 포함

## JSON 과 JSONP 의 차이점 ?

* JSON 은 Java String Object Notation 으로 데이터를 구조화된 데이터를 표현하기 위한 객체이며
* JSONP 는 Ajax 에서 CORS 이슈 발생시 우회 방법으로 사용하는 통신 방식이다.

## 자바스크립트의 Scope Chain 에 대해서 설명

* 변수가 접근 가능한 유효범위를 말한다.
* 함수단위로 유효범위가 변하며 내부 함수로 진입시 새로운 스코프가 Stack 형태로 구성된다.
* Scope Chain 은 하위에서 상위로 등록된 변수가 있는지 확인한다.

## 자바스크립트의 클로져란 ?

* 유효범위를 가지는 코드 블럭
* 상위의 스코프로 변수참조가 일어나는것을 말한다.

## 모듈 패턴에 대해서 설명

* 코드를 모듈화 시켜 변수의 범위를 제한하는 패턴
* `public` 과 `private` 한 유효범위를 가질 수 있다.

## 브라우저 랜더링 과정을 설명

* HTTP Request > (서버) > HTTP Response > HTML 파싱 > CSS / JS Request > 파싱 > DOM 트리 > 렌더트리 > 페인트

## 다음 상황에 대해 설명하시오

```text
서버는 응답을 빠르게 출력하고 있지만 웹 페이지가 늦게 뜨고 있다.
웹 사이트를 최적화 하기 위한 방법은 ?
```

* 서버 Request 횟수
* CSS / JS 를 minify 하여 사용
* gzip 전송
* 이미지 최적화 및 Lazy 로딩 사용
* CDN 사용
* JS 파일은 async / defer 사용
* 랜더링 최적화
* 마크업 복잡도를 단순화
* reflow 혹은 repaint 최소화

## 다양한 크기의 화면 대응 및 멀티 플렛폼에 대한 대응 방안 ?

* 각 디바이스별 최적화를 위한 방법들
* 반응형 디자인을 위한 미디어 쿼리를 사용

## ES5 / ES6 의 차이점은 ?

* const, let
* promise
* spread operator
* rest parameter

## screenX, pageX, clientX, offsetX, layerX 의 차이점은 ?

* screenX : 모니터 기준
* pageX : document 기준
* clientX & offsetX : 브라우저 기준
* offsetX : 타겟 기준

## 서버로부터 받은 응답은 잘 받은 상태지만 웹 페이지가 비정상 적으로 렌더링 되어 있다고 가정하면 어떤 문제가 있을까 ?

* JS 오류
* 무한루프
* 문법
* 비 정상 접근
* 서버 응답 오류
* DOM 파싱 오류
* 닫는 태그의 오류
* 문서모드 및 메타태그 정보 오류
* 페이지 인코딩

## querySelector 와 jQuery Selector 의 차이점 ?

* querySelector : 반환이 1개
* jQuery Selector : 반환값이 여러개 복수 (querySelectorAll 과 같음)
* querySelector 에서는 `class` 로 많이 사용을 안하고 `attribute` 로만 사용 (성능적인 측면 때문에 / data 속성이 제일 빠름)

## 자바스크립트에서 Iteration Method 에 대해서 설명

* `Symbol.Iterator` 속성을 갖는 객체를 Iterable 한 객체라고 한다.
* Array.Prototype.forEach : 모든 엘리먼트를 callback 에 넘겨 실행
* Array.Prototype.map : 인자로 넘겨진 엘리먼트를 새로운 배열로 리턴
* Array.Prototype.filter : 조건에 맞는 값들로 새로은 배열로 리턴

## 자바스크립트에서 var 를 사용하지 않으면 발생되는 현상 ?

* 전역 프로퍼티로 등록 된다.
* `use strict` (엄격모드) 구문을 사용하여 방지 가능하며 eslint 를 사용하면 동일한 효과
* 가장 큰 차이점은 삭제가 가능하다는 점

## RESTful 개발시 HTTP Method 를 설명

* POST : 리소스를 생성
* GET : 리소스를 요청
* PUT & PATCH : 리소스를 변경
* DELETE : 리소스를 삭제

## 그래픽 처리시에 백터와 비트맵의 차이점

* Vector : 방향기반 (SVG)
* Bitmap : 화소기반 (Canvas)

## SPA 에서의 뒤로가기

* 앵커나 해시뱅 (#!) 를 통한 히스토리 조작
* `pushState` 를 이용한 히스토리 조작 방법

## Promise 란 ?

* 비동기로 작업을 순차적으로 처리하기 위한 패턴
* `then` `then` 구문으로 사용