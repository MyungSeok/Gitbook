---
description: 자바스크립트의 연산자 및 표현식을 정의합니다.
---

# Operator & Expression

## In

`in` 연산자는 명시된 속성이 객체에 존재하면 `true` 를 반환합니다.

```javascript
속성 in 객체명
```

* 속성
  * 속성의 이름이나 배열의 인덱스를 뜻하는 문자열 또는 수의 값입니다.
* 객체명
  * 객체의 명칭

{% tabs %}
{% tab title="Example 1" %}
```javascript
var arrayObj = ['a', 'b', 'c'];

console.log(3 in arrayObj);    // false
console.log(0 in arrayObj);    // true

console.log('a' in arrayObj);    // false
console.log('length' in arrayObj);    // true
```
{% endtab %}

{% tab title="Example 2" %}
```javascript
var color1 = new String('green');
console.log('length' in color1);    // true

var color2 = 'Red';
console.log('length' in color2);    // false
// color2 는 String 객체가 아니기 때문에 오류를 발생함
```

`String` 생성자로 만들어진 문자열을 명시할 수 있지만 _**문자열 리터럴은 명시할 수 없다**_
{% endtab %}

{% tab title="Example 3" %}
```javascript
console.log('toString' in {});     // true
```

프로토타입 체인에 의하여 접근 가능한 속성은 `true` 를 반환합니다.
{% endtab %}
{% endtabs %}

## InstanceOf

`instanceof` 연산자는 생성자의 `prototype` 속성과 묶인 프로토타입을 가진 오브젝트인지 확인합니다.

```javascript
object instanceof constructor
```

* object
  * 테스트 대상인 오브젝트
* constructor
  * 테스트할 함수 \(프로토타입 오브젝트\)

{% tabs %}
{% tab title="Example 1" %}
```javascript
function C() {};

var obj = new C();

console.log(obj instanceof C);    // true
```
{% endtab %}

{% tab title="Example 2" %}
```javascript
function Car(make, model, year) {
  this.make = make;
  this.model = model;
  this.year = year;
}
var auto = new Car('Honda', 'Accord', 1998);

console.log(auto instanceof Car);  // true

console.log(auto instanceof Object);  // true
```
{% endtab %}
{% endtabs %}

## Typeof

`typeof` 연산자는 피연산자 타입을 가르키는 문자열을 반환합니다.

```javascript
typeof 피연산자
```

| 타입 | 결과 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Undefined | "undefined" |
| Null | "object" |
| String | "string" |
| Number | "number" |
| Boolean | "boolean" |
| Function Object | "function" |
| other Object | "object" |

