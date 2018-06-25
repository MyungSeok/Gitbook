---
description: 자바스크립트 디자인 패턴
---

# Design Pattern

## 네임스페이스 패턴

지역/전역 객체를 선언하여 그 안에 값을 삽입하여 사용하는 것

{% tabs %}
{% tab title="권장 패턴" %}
```javascript
var App = App || {};
App.Parent = function () {};
App.Child = function () {};

App.container = 1;
App.module = {
    module_1: {
        data: {a: 1, b: 2}
    },
    module_2: {}
};
```
{% endtab %}

{% tab title="안티 패턴" %}
```javascript
function Parent() {} 
function Child() {} 

var some_var = 1;

var module1 = {}; 

module.data = {a : 1, b : 2}; 

var module2 = {}
```
{% endtab %}
{% endtabs %}

## 모듈 패턴

`public` 과 `private` 의 접근 권한을 가능하게 한다.

```javascript
(function () {
    // private 변수들과 함수들을 선언
    
    return {
        // public 변수들과 함수들을 선언
    };
}());
```

{% tabs %}
{% tab title="Example 1" %}
```javascript
var HTMLChanger = (function() {
    var contents = 'contents';
    
    var changeHTML = function () {
        var element = document.getElementById('attribute-to-change');
        element.innerHTML = contents;
    }
    
    return {
        callChangeHTML: function () {
            changeHTML();
            console.log(contents);
        }
    };
}());

HTMLChanger.callChangeHTML();         // 'contents'
console.log(HTMLChanger.contents);    // undefined
```
{% endtab %}
{% endtabs %}

## 커링 \(Currying\)

여러개의 인자를 받는 함수가 있을 경우 일부의 인자만 받는 함수를 만드는 기법

```javascript
function volume(l, w, h) {
    return l * w * h;
}

function curry(fn) {
    var arity = fn.length;
    
    return (function resolver() {
        var memory = Array.prototype.slice.call(arguments);
        
        return function () {
            var local = memory.slice();
            
            Array.prototype.push.apply(local, arguments);
            
            var next = (local.length >= arity? fn : resolver);
            
            return next.apply(null, local);
        };
    }());
}
```

{% tabs %}
{% tab title="Case 1" %}
```javascript
var curried = curry(volume),
    length = curried(2),
    lengthAndWidth = length(3);
    
console.log(lengthAndWidth(4));
```
{% endtab %}

{% tab title="Case 2" %}
```javascript
var _curried = curry(volume);

console.log(_curried(2)(3)(4));
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
`Case 2` 가 10배정도 빠름
{% endhint %}

