---
description: 자바스크립트의 객체 생성자
---

# Object

## assign

`assign()` 메소드는 열거할 수 있는 하나의 이상의 소스 오브젝트의 프로퍼티들을 복사합니다.

```javascript
Object.assign(target [, sources]) 
```

* target
  * 타겟 오브젝트
* sources
  * 하나 이상의 소스 오브젝트

{% tabs %}
{% tab title="Example 1" %}
```javascript
var obj = {a: 1};
var cp_obj = Object.assign({}, obj);

console.log(cp_obj);
// {a: 1}
```
{% endtab %}

{% tab title="Example 2" %}
```javascript
var obj1 = { a: 1 };
var obj2 = { b: 2 };
var obj3 = { c: 3 };

var obj = Object.assign(o1, o2, o3);

console.log(obj); 
// { a: 1, b: 2, c: 3 }

console.log(obj1);  
// { a: 1, b: 2, c: 3 }, 타겟 오브젝트, 그 자체도 변화합니다.
```
{% endtab %}

{% tab title="Example 3" %}
```javascript
var obj1 = { a: 1, b: 1, c: 1 };
var obj2 = { b: 2, c: 2 };
var obj3 = { c: 3 };

var obj = Object.assign({}, obj1, obj2, obj3);

console.log(obj); 
// { a: 1, b: 2, c: 3 }
```
{% endtab %}
{% endtabs %}

## hasOwnProperty

`hasOwnProperty()` 메소드는 객체가 특정 프로퍼티를 가지고 있는지 확인 합니다.

```text
Object.hasOwnProperty(prop)
```

* prop
  * 확인 하려는 프로퍼티 명칭

{% tabs %}
{% tab title="Example 1" %}
```javascript
var obj = new Object();
obj.prop = 'exists';

obj.hasOwnProperty('prop'); // true
delete obj.prop();
obj.hasOwnProperty('prop'); // false
```
{% endtab %}

{% tab title="Example 2" %}
```javascript
var obj = new Object();
obj.prop = 'exists';

obj.hasOwnProperty('prop'); // true

// 상속된 프로퍼티는 검사할 수 없다.
obj.hasOwnProperty('toString'); // false
obj.hasOwnProperty('hasOwnProperty'); // false
```
{% endtab %}

{% tab title="Example 3" %}
```javascript
var obj = {
  hasOwnProperty: function() {
    return false;
  },
  bar: 'Here be dragons'
};

foo.hasOwnProperty('bar'); // false

({}).hasOwnProperty.call(foo, 'bar'); // true

Object.prototype.hasOwnProperty.call(foo, 'bar'); // true
```
{% endtab %}
{% endtabs %}



