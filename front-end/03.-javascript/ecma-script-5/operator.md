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
{% endtabs %}

