# ECMA 6

## Arrows

### Description

화살표 함수 표현식은 축약형 함수 입니다.

### Syntax

```javascript
(param1, param2, ... , paramN) => { statements }
```

#### Parameters 

* statements
  * 함수의 내용

### Example 

{% tabs %}
{% tab title="Case 1" %}
```javascript
// 매개변수가 하나 이상있는 경우는 괄호가 필요
(param1, param2) => {
    return param1 + param2
};

// 매개변수가 하나인 경우에는 괄호가 필요 없음
param1 => {
    return param1 + 1
}

// 매개변수가 없을경우
() => {
    console.log('Hello World');
}
```
{% endtab %}

{% tab title="Case 2" %}
```javascript
var list = [2, 4, 6, 8];

// Expression Block 사용 안함 (표현식의 결과가 반환됨)
var odd = list.map(value => value + 1); // [3, 5, 7, 9]

// Expression Block 사용 (블럭 내부만 실행, 반환값을 위해서는 return 표현식을 명시해야 함)
list.forEach(v => {
    console.log(v);
});

```
{% endtab %}
{% endtabs %}

### Expression

* 선언 컨텍스트의 밖의 `this` 값을 가진다.
  * `this` 가 바인딩 되지 않는다.

```javascript
function foo() {
    this.value = 0;
    
    setInterval(() => {
        console.log(this.value);    // 0
    }, 1000);
}
```

* 생성자 \(constructor\) 로 사용될수 없다. \(new 연산자 사용 불가\)

```javascript
var Foo = () => {};
var foo = new Foo();    // TypeError : Foo is not a constructor
```

## Default Parameter

### Description

함수의 매개변수의 기본값이 설정 가능합니다.

### Syntax

```javascript
function func_name([param1[= defaultValue1][, ... , paramN[= defaultValueN]]]) {
    statements
}
```

#### Parameters 

* func\_name
  * 함수명 
* param1, param2
  * 파라메터 명
* defaultValue1, defaultValue2
  * 파라메터 기본값
* statements
  * 함수의 내용

### Example 

{% tabs %}
{% tab title="Case 1" %}
```javascript
function add(a, b = 1) {
    return a * b;
}

console.log(add(5)) // 5
```
{% endtab %}
{% endtabs %}

### Expression

* 함수에도 적용 가능하다. 

```javascript
function callLog(msg = defaultMsg()) {
    return console.log(mes);
}

function defaultMsg() {
    return 'TEST_LOG';
}

callLog()     // TEST_LOG
```

* `undefined` 전달 시 

```javascript
function callLog(msg = 'TEST_LOG') {
    return console.log(mes);
}

callLog(undefined)     // TEST_LOG
```

## Spread Operator 

2개 이상의 인수를 나열하는 방식

### Syntax

```javascript
// 함수 호출용
myFunction(...args);

// 배열 리터럴용
[...args, 5, 6, 7];

// 비 구조화용
[a, b, ...args] = [1, 2, 3, 4, 5];
```

### Example

{% tabs %}
{% tab title="Case 1" %}
```javascript
var org = [3, 4];
var custom = [1, 2, ...org, 5];    // [1, 2, 3, 4, 5]
```
{% endtab %}
{% endtabs %}

### Expression

* 스프레드 연산자로 배열 & 객체 복제. 

```javascript
var array = [1, 2, 3];

var cloneArray = [...array];
console.log(cloneArray);    // [1, 2, 3]

var obj = {a: 10, b: 20};

var cloneObj = {...obj};
console.log(cloneObj);    // {a: 10, b: 20}
```

## Rest Parameter

나머지 매개변수 \(rest parameter\) 구문에 나머지 인수들도 정의해 나타냅니다.

### Syntax

```javascript
function (a, b, ...theArgs) {
    // statements
}
```

### Example 

{% tabs %}
{% tab title="Case 1" %}
```javascript
function foo(...Args) {
    console.log(Args.length);
}

foo();           // 0
foo(5);          // 2
foo(5, 7, 9);    // 3
```
{% endtab %}

{% tab title="Case 2" %}
```javascript
function foo(arg1, ...Args) {
    return Args.map(function (elem) {
        return arg1 * elem
    });
}

console.log(foo(2, 1, 2, 3));    // [2, 4, 6]
```
{% endtab %}
{% endtabs %}

### Expression

* `arguments` 객체가 아닌 `Array` 객체의 `method` 사용이 가능하다.

```javascript
function sortRestArgs(...Args) {
    return Args.sort();
}

function sortArguments() {
    return arguments.sort();
}

console.log(sortRestArgs(5, 3, 7, 1));        // [1, 3, 5, 7]

console.log(sortArguments(5, 3, 7, 1));        // TypeError
```

## Destructuring Syntax

구조분해 문법은 ES6 에서 사용되는 변수의 선언 방식입니다.

### Expression

* 특정 객체의 값을 꺼내오는 방법

{% tabs %}
{% tab title="ECMA 5" %}
```javascript
var josh = {
  language: 'javascript',
  position: 'front-end',
  area: 'pangyo',
  hobby: 'singing',
  age: '102'
};

var language = josh.language;
var position = josh.position;
var area = josh.area;
var hobby = josh.hobby;
var age = josh.age;
```
{% endtab %}

{% tab title="ECMA 6" %}
```javascript
var josh = {
  language: 'javascript',
  position: 'front-end',
  area: 'pangyo',
  hobby: 'singing',
  age: '102'
};

var { language, position, area, hobby, age } = josh;

console.log(language); // javascript
console.log(position); // front-end
console.log(area); // pangyo
console.log(hobby); // singing
console.log(age); // 102
```
{% endtab %}
{% endtabs %}

* 함수의 적용

```javascript
var context = {
    commit: actionName => console.log(actionName + ' has been committed!!')
};

var {commit} = context;
commit('addProducts');     // addProducts has been committed !!
```

## Export Syntax

지정된 파일에서 객체 \(함수, 오브젝트, 원시타입\) 을 `export` 하는데 사용된다.

### Syntax

```javascript
// Named Exports
export { myFunction };              // 함수 exports
export const foo = Math.sqrt(2);    // 상수 exports

// Default Exports (스크립트에서 유일하게 한번 사용)
export default myFunctionOrClass;
```

