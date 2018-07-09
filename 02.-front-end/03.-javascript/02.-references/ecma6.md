# ECMA 6

## arrows

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

