# Symbol & Iterator & Generator

## Symbol

ES6 에서 나온 원시 데이터형 ([Primitive DataType](https://developer.mozilla.org/en-US/docs/Glossary/Primitive)) 의 일종으로 객체에 `Unique` 한 속성을 만들어 다른 라이브러리와 충동을 피하기 위함이다.

* Undefined
* Null
* Boolean
* Number
* String
* Object
* _**Symbol**_

### Syntax

```javascript
Symbol([description]);
```

#### Parameter

* description
  * 선택적 (Optional) 문자열로 디버깅에 사용할 수 있는 설명이다.
  * 자체적으로 심볼에 접근하는 용도로 사용할 수 없음 

### Description

기본적으로 새 원시 심볼을 생성하려면 아래와 같이 선택적 문자열과 함께 `Symbol()` 을 쓰면 된다.

```javascript
var sym1 = Symbol();
var sym2 = Symbol('foo');
var sym3 = Symbol('foo');
```

매번 새로운 심볼을 생성하기 때문에 아래 같이은 조건은 성립할 수 없다.

```javascript
console.log(Symbol('foo') === Symbol('foo'))      // false
```

`new` 연산자를 이용한 문법은 `TypeError` 를 발생한다.

```javascript
var sym = new Symbol();     // TypeError
```

반드시 심볼 래퍼 객체 생성이 필요하면 Object() 함수를 이용하여 사용가능하다.

```javascript
var sym = Symbol('foo');
typeof sym;               // "symbol"
var symObj = Object(sym);
typeof symObj;            // "object"
```

### 심볼의 생성

심볼의 생성은 다음 3가지 방법이 있다.

#### 고유한 심볼 생성

```javascript
var sym = Symbol('foo');
```

#### 심볼 레지스트리에서 찾아서 복사

```javascript
var sym = Symbol.for('foo');
```

#### 미리 정의된 상용 심볼 사용

```javascript
Symbol.iterator
```

상용심볼은 특별한 용도를 위해서 만들어 놓은 심볼이며 대표적인 상용 심볼은 다음과 같다.

* Symbol.iterator
  * 이터러블한 객체를 정의하기 위한 심볼
* Symbol.hasInstance
  * [`instanceof`](/02.-front-end/03.-javascript/02.-references/operator-and-expression.html?h=instanceof) 를 확장하기 위한 심볼
* Symbol.match
  * [`String.prototype.match`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/match) 메소드의 확장

## Iterator

자바스크립트의 반복문의 `for loop` 는 다음 몇가지로 나뉜다.

* for
  * 가장 기본적인 `for loop`
* forEach
  * 배열을 순회하며 `value` 와 `index` 를 매개변수로 전달한다.
  * `break`, `return` 으로 루프를 중단할 수 없다.
* for in
  * 배열의 인덱스만 순환 하는것이 아닌 프로토타입 체인을 포함한 모든 속성을 순회한다.
  * _**배열보다는 객체를 순회**_ 하기 위해 만들어진 루프이다.
* for of
  * `for in` 으로 배열을 순회할 때 생기는 문제점들을 해소하였다.

> `for of` 는 _**순회가능한 (iterable) 객체를 상대로 사용 가능**_ 하다.

순회가능한 (Iterable) 한 객체는 _**`Symbol.iterator` 심볼을 속성으로 가지고 있으며 이터레이터 객체를 반환하는 객체**_ 를 뜻한다.  
해당 스팩을 _**이터러블 프로토콜**_ 이라고 하며 _**해당 스팩을 구현한 객체를 이터러블 객체**_ 라고 한다.

### Iterator Object

#### Iterator Spec

* `next()` 메소드를 구현하고 있다.
* `done` 과 `value` 속성을 가진 객체를 반환한다.

#### Example

영원히 `0` 을 반환하는 Iterator

```javascript
var zeroIterator = {
  [Symbol.iterator]: function () {
    return this;
  }, 
  next: function () {
    return {done: false, value: 0};
  }
}
```

> Reference  
> http://www.bsidesoft.com/?p=2913  
> https://youtu.be/CY_2mFxQwzc

## Generator


> Reference  
> https://gist.github.com/qodot/ecf8d90ce291196817f8cf6117036997