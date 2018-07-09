# 01. General

## 일급객체 \(First-Class Object\)

자바스크립트는 일급객체 \(First-Class Object\) 입니다.  
일급 객체 \(First-Class Object\) 는 다음과 같은 특징을 갖습니다.

* 일급 객체는 _**변수에 저장 가능**_ 해야 한다.
* 일급 객체는 _**함수의 파라미터로 전달**_할 수 있어야 한다.
* 일급 객체는 _**함수의 반환값으로 사용**_할 수 있어야 한다.
* 일급 객체는 _**자료구조에 저장**_할 수 있어야 한다.

## JSONP

웹 브라우저는 _**SOP \(same origin policy: 동일출처정책\)**_ 에 따라 서로 다른 도메인간의 데이터 통신을 제한하고 있다   
script 코드가 _**DOM 트리에 추가되어 실행되면 외부 스크립트를 로드할 수 있다는 것**_ 에서 착안   
`<script>` 태그는 SOP 정책에 속하지 않기 때문에 jsonp \(json width padding\) 이 사용됨

![](../../../.gitbook/assets/undefined%20%282%29.tiff)

{% hint style="warning" %}
JSONP 의 callback 은 _**서버에서 지원**_ 해줘야 정상적으로 사용이 가능
{% endhint %}

{% tabs %}
{% tab title="Case 1" %}
#### 요청 URL 뒤에 callback 파라메터 추가하여 jsonp 요청 구현하기

#### Client

```javascript
$.getJSON('/jsonp.json?callback=?', function (data) {
    console.log('success: ', data);
});
```

#### Server

```java
private void doGet(HttpServletRequest request, HttpServleteResponse response) throws ServletException, IOException { 
    request.setCharacterEncoding("UTF-8");
    response.setCharacterEncoding("UTF-8");
          
    String id = request.getParameter("id");
    String callBack = request.getParameter("callback");
  
    JSONObject obj = new JSONObject();
    obj.put("result", id);
    obj.put("go", "테스트");
          
    PrintWriter out = response.getWriter();
    out.write(callBack + "(" + obj.toString() + ")");
    System.out.println(callBack + "(" + obj.toString() + ")");
    out.flush();
    out.close();
}
```
{% endtab %}

{% tab title="Case 2" %}
#### 요청 json 에 callback 함수로 한번 감싸서 jsonp 구현하

#### Client

```javascript
$.ajax({
  url: "/jsonp.json",
  dataType: 'jsonp',
  jsonpCallback: "myCallback",
  success: function(data) {
    console.log('성공 - ', data);
  },
  error: function(xhr) {
    console.log('실패 - ', xhr);
  }
});
```

#### Server

```java
myCallback({"message":"You got an AJAX response via JSONP from another site!"});
```
{% endtab %}

{% tab title="Case 3" %}
#### jsonpCallback 옵션 없이 사용하기

#### Client

```javascript
$.ajax({
  url: "/jsonp.json",
  dataType: 'jsonp',
  success: function(data) {
    console.log('성공 - ', data);
  },
  error: function(xhr) {
    console.log('실패 - ', xhr);
  }
});
```

#### Server

```java
jQuery18305806868467951786_1366340807385({"key":"value"});
```
{% endtab %}
{% endtabs %}

## 암묵적 전역

자바스크립트 내에 변수 선언시에 선언자 \(`var`\) 가 없으면 _**암묵적 전역**_ 으로 인해 전역 프로퍼티로 등록 된다.

```javascript
var a = 0;
b = 2;
(function () {
    c = 3;
}());

delete a;
delete b;
delete c;

console.log(typeof a);        // number
console.log(typeof b);        // undefined
console.log(typeof c);        // undefined
```

{% hint style="info" %}
프로퍼티는 `delete` 연산자로 삭제 가능
{% endhint %}

## 상속 \(Inheritance\)

자바스크립트에는 자바와 달리 `class` 가 존재하지 않아 `prototype` 을 사용하여 class 를 구현합니다.

#### 상속 Class 생성 

```javascript
function Shape() {
    this.x = 0;
    this.y = 0;
}

Shape.prototype.move = function (x, y) {
    this.x += x;
    this.y += y;
}

function Rectangle() {
    Shape.call(this);
}

Rectangle.prototype = Object.create(Shape.prototype);
Rectangle.prototype.constructor = Rectangle; 
```

#### 상속 객체 생성

```javascript
var rect = new Rectangle();

console.log(rect instanceof Rectangle);
console.log(rect instanceof Shape);

rect.move(1, 1);
```

## 호이스팅 \(Hoisting\)

자바스크립트 엔진이 실행 컨텍스트를 생성하면서 scope 를 정의할 때 기술된 순서에 상관없이 _**선언부에 대한 처리 해석의 우선순위를 최우선으로 끌어올려 먼저 해석**_ 하는 것   
이는 다음과 같은 특징을 갖는다.

* 변수의 정의가 그 범위에 따라 _**선언과 할당으로 분리**_ 한다.
* 선언과 할당이 분리되며 에러를 야기시킬 수 있다.
* ES6 에서는 호이스팅의 지원이 없어졌다.
* 기존 ES5 에서는 호이스팅이 있어 해당 값을 선언 후 호출하면 undefined 로 나온다.

#### 예제 코드 

```javascript
var value = 'outer scope';
(function () {
    console.log(value);        // undefined
    var value = 'inner scope';
});
```

위 코드는 아래와 같이 해석 된다.

```javascript
var value = 'outer scope';
(function () {
    var value;

    console.log(value);        // undefined    
    var value = 'inner scope';
});
```

## 익명 함수 \(Anonymouse Function\)

함수의 선언이 아닌 _**함수 표현식을 이용하는 방법**_ 이며 즉시 실행 구문을 만들때 많이 사용된다.

익명 함수는 동적으로 할당되는 유효범위를 가지기 때문에 _**강제적인 유효범위를 설정 하는 경우에도 사용**_ 된다.

```javascript
(function () {
    var value = 'Hello World';
}());

console.log(value);     // ReferenceError: value is not defined
```

## 즉시 실행 구문 \(IIFE : Immediately-Invoked Function Expression\)

익명 함수 \(Anonymouse Function\) 를 이용하여 _**바로 실행 가능한 함수 표현식을 이용**_ 하여 만들어 내는 구문

#### 익명 함수 표현식 

```javascript
(function () {
    /* 실행코드 */ 
}());
```






